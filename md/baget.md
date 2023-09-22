# nuget server
setup own nuget server with docker
<br/>
https://loic-sharma.github.io/BaGet/installation/docker/


# How to upload package

1. spec project<br/>
`nuget spec <name>.csproj`

2. pack nuspec to nupkg<br/>
`dotnet pack`
<br/>nupkg file will show up in /bin/debug folder

3. goto /bin/debug and upload nupkg to nuget server<br/>
`dotnet nuget push -s http://localhost:5555/v3/index.json -k [key_ที่อยู่ในไฟล์ baget.env] [package_name].nupkg`
<br/>
`dotnet nuget push -s http://localhost:5555/v3/index.json -k c2FyYW5wb25na0BhZW9uLmNvLnRo com.aeonth.lib.servicetoken.1.0.0.nupkg`
