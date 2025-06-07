### [Optional] seed the database
Use [seed_database.sql](.devcontainer/seed_database.sql) to seed the dev database.

To validate use ```psql -h db -U $PGUSER``` to connect to db.

### Setup instructions
1. Load the devcontainer

### create the react app in the container
```zsh
npx create-react-app <appname>
```

### setup proxy for react frontend to communicate with dotnet backend
Add a proxy field to your React app's package.json to handle API calls to the .NET backend:

```json
{
  "name": "your-react-app",
  "version": "0.1.0",
  "private": true,
  "proxy": "http://localhost:5000",
  "dependencies": {
    // ... your dependencies
  }
}
```

This proxy configuration allows your React app (running on port 3000) to make API calls to your .NET backend (running on port 5000) without CORS issues during development.

Alternatively, you can create a setupProxy.js file in the src folder for more advanced proxy configuration:

```javascript
const { createProxyMiddleware } = require('http-proxy-middleware');

module.exports = function(app) {
  app.use(
    '/api',
    createProxyMiddleware({
      target: 'http://localhost:5000',
      changeOrigin: true,
    })
  );
};
```

Note: You'll need to install http-proxy-middleware if using setupProxy.js:
```zsh
npm install --save-dev http-proxy-middleware
```

### create dotnet webapi
```zsh
dotnet new webapi -o <project_name> --use-controllers --use-program-main
```

### create dotnet gitignore
```zsh
dotnet new gitignore
```

### create new controller
```zsh
dotnet new apicontroller --actions --name <controller name>
```

### for devmode, enable cors
```csharp
app.UseCors(builder => 
  builder.AllowAnyOrigin()
      .AllowAnyMethod()
      .AllowAnyHeader()
);
```
