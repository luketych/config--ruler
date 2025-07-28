## Use feathers cli to add users, re-register and register services, etc.

When creating an application (e.g. `my-app`) with `npm create feathers@latest my-app`the Feathers CLI will be installed locally into your new project. This is preferred over global installation so that everybody working on your project has the same version and commands available by running `npx feathers`.

#### Set up Feathers authentication and a users service. This is required for any other service that needs authentication.

```
npx feathers generate authentication
```

```
npx feathers generate service
```

```
npx feathers generate hook
```

#### Set up a new database connection. This is already done when creating a new application but you can still set up other databases.

```
npx feathers generate connection
```
