# nuget server
setup own nuget server with docker
<br/>
https://loic-sharma.github.io/BaGet/installation/docker/

<br/>

# How to upload package

1. spec project<br/>
`nuget spec <name>.csproj`

3. pack nuspec to nupkg<br/>
`dotnet pack`

4. upload to nuget server<br/>
`dotnet nuget push -s http://localhost:5555/v3/index.json -k [key_ที่อยู่ในไฟล์ baget.env] [package_name].nupkg`
