# Update Project Dependencies

Updating the dependencies is a tedious job. This doc is intended to help streamline the process and make it painless.

## Maintain Update Log

There's a sample `Update Log` at the end of this document. Create a new file where you can dump the Version Diff, Test results, Chrome/Node/npm versions. Mention the dependencies that you had to roll back along with the reason. Optionally you can mention the errors/warnings that you encountered while updating dependencies.

## Managing Node Versions

It is recommended that you use [Node Version Manager](https://github.com/creationix/nvm) or [Node Version Control](https://github.com/tj/n) to switch node versions quickly in order to run and test this project on multiple node versions.

## Update Tooling

**Update npm:**

1.  Run `npm install -g npm`
2.  Run `npm -v` and record npm version in `Update Log`.

**Update Chrome**

1.  Download the [latest version](https://www.google.com/chrome/browser/desktop/index.html) or go to [chrome://settings/](chrome://settings/) and update.

2.  Go to `Chrome -> About` and record version number in `Update Log`

## Update Dependencies

[npm-check-updates](https://github.com/tjunnone/npm-check-updates) is a great tool to update your dependencies. It will only update your `package.json`. Run `npm install` if you want to install updated package versions. There are 3 useful commands.

1.  `ncu -u --semverLevel minor`
2.  `ncu -u --semverLevel major`
3.  `ncu -u`

Confirm/adjust eslint-config-airbnb compatible [dependency versions](https://www.npmjs.com/package/eslint-config-airbnb)

`npm info "eslint-config-airbnb@latest" peerDependencies`

## Correct Errors and Rollback Dependencies

Run `npm install` to install updated versions and then start the example app by running `npm start`. Make sure that the project is running smoothly. If not, track down the dependencies that are causing problems and try to roll them back one by one and check if the example application is running.

Note down the rolled back dependencies and state the reason in your `Update Log`.

## Full Regression Testing

Most of the errors/warnings would go away once you roll back the problemetic dependencies. But we need to make sure that the internal commands, tools, scaffolding etc. are functional too.

**Example App:**

- `rm -rf node_modules && rm package-lock.json`
- `npm install && npm start`

- Browse example app on development server
  - Browse Features page, change language to `de`
  - Browse NotFound page
- Browse example app on dev tunnel
- Browse example app on Production server
- Browse example app offline

Identify problems that occur and try to resolve them by rolling back the respective dependencies. Update the `Update Log`.

**Internal Commands:**

- `npm run clean` (Be careful, this will commit all your changes.)
- `npm run generate component` TestComp /w defaults
- `npm run generate container` TestPage /w defaults
- Add a new route in the App container:

```js
import TestPage from 'containers/TestPage/Loadable';

<Route path="/test" component={TestPage} />;
```

- Use TestComp on TestPage -> bypass all tests in TestComp and TestPage (set true = true)
- `npm start` > `localhost:3000/test`
- `npm test` (expect test failure due to incomplete test coverage)
- `npm run build`
- `npm run start:prod` > `localhost:3000/test`

# Sample Update Log

## Tooling Versions

- Node 8.11.4
- npm 6.4.0
- Mac OS 10.13.6
- Chrome 68.0.3440.106 (64-bit)

## :spiral_notepad: Notes

1.  `react-router` was not updated. Thanks to @anuraaga for all his work. Ref- #1746
2.  `history` was not updated because of `react-router v3`'s dependency on it. Should go away when #1746 is merged.
3.  `react-test-renderer` was added as a dev-dependency because enzyme was showing warnings-
    > A few deprecation warnings were added in React 15.5. This supports the new APIs that React recommends. Ref. [#876](https://github.com/airbnb/enzyme/pull/876)
4.  If you see a package-name being repeated, note that the version number of the last occurrence will get precedence.

## :package: Version Diff

**[0] PATCH UPDATES**



**[1] MINOR UPDATES**



**[3] MAJOR UPDATES**



**[4] ROLLBACKS**

```
 history                                     3.3.0  →       4.6.1 <--- rolled back
 react-router                                3.0.5  →       4.1.1 <--- rolled back
 image-webpack-loader                        2.0.0  →       3.0.0 <--- rolled back
```

**[5] NEW DEPENDENCIES**

```
react-test-renderer                                     15.5.4
```

## Errors Encountered


