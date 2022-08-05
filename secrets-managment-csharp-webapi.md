# Secrets Managment

Secrets Management is for **development** only

It allows a project to use resources like connection strings and passwords without embedding them 
in the code or in configuration files that will be stored in repositories.

Secrets can be read into the program at runtime.

Secrets will override appsettings.json file data. Meaning if a key value of "webapi" exists in the 
appsettings.json and there is a secret with the key "webapi", the secret will be read rather than
the appsettings.json.

To initiate secrets management for a project:
- create the project
- in the project folder, type `dotnet user-secrets init`

To create a secret for the project:
- `dotnet user-secrets set "key" "value"` (i.e. `dotnet user-secrets set "webapi" "ABC123"`)
