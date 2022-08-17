# Warren - .NET Pack and Push :package:

This action is responsible for build, pack and publish all packages within a Solution.

## Inputs

### `solution`

**Required**: Solution file name without the **.sln** extension

### `project`

**Required**: Projects file name without the **.nupkg** extension

### `pkg-version-suffix`

**Required**: The version suffix command with value

### `nuget-source-name`

**Required**: The nuget source to publish the package (configured by [warrenbrasil/dotnet-config@v1](https://github.com/marketplace/actions/warren-configure-net-sdk) action)

## Usage

```yml
- name: Warren - .NET Pack and Push
  uses: warrenbrasil/dotnet-pack@v1
  with:
    solution: Warren.Core.MyRepo
    project: Warren.Core.MyRepo
    pkg-version-suffix: --version-suffix beta
    nuget-source-name: ${{ secrets.NUGET_SOURCE_NAME }}
```

## Troubleshooting

Sometimes, the `dotnet pack` command tries to pack `csproj` files that aren't really packable. To solve this add the `<IsPackable>false</IsPackable>` to the `PropertyGroup` tag that contains project metadata for all projects that shouldn't be packed.

```csproj
<PropertyGroup>
  <TargetFramework>net6.0</TargetFramework>
  <IsPackable>false</IsPackable>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```
