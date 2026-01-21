### [Optional] seed the database
Use [seed_database.sql](.devcontainer/initdb.d/seed_database.sql) to seed the dev database.

To validate use ```psql -h db -U $PGUSER``` to connect to db.

### Run the first time setup (automatic for devcontainer, only required for manual setup)
```make -C .devcontainer makefile```

### Project Setup instructions
1. Load the containers
    a. Load the devcontainer
    b. (or) use docker compose ```docker compose up --build --force-recreate -d```

2. [Optional] Setup claude code using ```claude``` command

### create the react app in the container
```zsh
npx create-react-app <appname>
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
