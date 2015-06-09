# dokku-newrelic

## Configuration

To track your deployments on New Relic you need to configure two environments vars:

    dokku config:set appname NEW_RELIC_API_KEY=your-api-key

And at least one of these:

    dokku config:set appname NEW_RELIC_APP_NAME=your-application-name

Like any configuration vars in dokku they will be exported so you can use it in your
application tracking.

```js
/**
 * New Relic agent configuration.
 *
 * See lib/config.defaults.js in the agent distribution for a more complete
 * description of configuration variables and their potential values.
 */
exports.config = {
  /**
   * Array of application names.
   */
  app_name : [ process.env.NEW_RELIC_APP_NAME ],
  /**
   * Your New Relic license key.
   */
  license_key : process.env.NEW_RELIC_LICENSE_KEY,
  logging : {
    /**
     * Level at which to log. 'trace' is most useful to New Relic when diagnosing
     * issues with the agent, 'info' and higher will impose the least overhead on
     * production applications.
     */
    level : 'trace'
  }
};
```

