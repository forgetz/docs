# nuget server
setup own nuget server with docker
https://loic-sharma.github.io/BaGet/installation/docker/

<br/>

# How to upload package

1. spec project
`nuget spec <name>.csproj`

2. pack nuspec to nupkg
`dotnet pack`

3. upload to nuget server
`dotnet nuget push -s http://localhost:5555/v3/index.json -k [key_ที่อยู่ในไฟล์ baget.env] [package_name].nupkg`
