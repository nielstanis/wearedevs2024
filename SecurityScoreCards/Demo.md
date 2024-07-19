# SecurityScoreCard CLI & API demo

The security scorecard installation steps can be found here:

In order to generate scorecard without any restrictions `GITHUB_AUTH_TOKEN` needs to be set and will be used to perform all checks. 

- `scorecard --repo=https://github.com/JamesNK/Newtonsoft.Json` 
- `scorecard --nuget newtonsoft.json`
- `scorecard --nuget newtonsoft.json --format json >> newtonsoft.json`

It's also possible to fetch the output from the online viewer by OpenSSF: 
https://securityscorecards.dev/viewer/?uri=github.com%2FJamesNK%2FNewtonsoft.Json

# Deps.dev

Combines some of the data on versions and OpenSSF scorecard and makes it available; no need to have tools run checks for you.

- https://deps.dev/nuget/newtonsoft.json

It also has API available to get all data based on ecosystem. 

- `https://api.deps.dev/v3/systems/nuget/packages/newtonsoft.json`
- `https://api.deps.dev/v3/systems/nuget/packages/newtonsoft.json/versions/13.0.2`
- `https://api.deps.dev/v3/projects/github.com%2Fjamesnk%2Fnewtonsoft.json`