# Connect Server To Database

- [ ] Navigate to “Database Deployments”
- [ ] Click “Connect”
- [ ] Click “Connect Your Application”
- [ ] Select “C# / .NET” for the driver
- [ ] Select “2.13 or later” for the version
- [ ] Copy the connection string
- [ ] Add the connection string to `Secrets.json`

```json
// Secrets.json
var settings = MongoClientSettings.FromConnectionString("mongodb+srv://samyatiwari:<password>@cluster0.bvp10gl.mongodb.net/?retryWrites=true&w=majority");
settings.ServerApi = new ServerApi(ServerApiVersion.V1);
var client = new MongoClient(settings);
var database = client.GetDatabase("test");


{
  "ConnectionStrings": {
    "CommBank": "{CONNECTION_STRING}"
  }
}
```
