
Invocación del servicio WebAPI
==============================

A continuación, se muestra ejemplos de consumo del servicio WebAPI en C#:

Ejemplo: ValidarCredenciales

.. code-block:: javascript

    using (HttpClient client = new HttpClient())
        {
            client.BaseAddress = new Uri("https://VJ.legisoffice.com/LoServiceVJ/");

            var model = new AutenticacionModel() { Usuario = "admin", Clave = "123", Proveedor = "Nombre del proveedor" };
            var content = new StringContent(JsonConvert.SerializeObject(model), Encoding.UTF8, "application/json");
            var response = client.PostAsync("vj/ValidarCredenciales", content).Result;

            if (response.IsSuccessStatusCode)
                {
                    string result = response.Content.ReadAsStringAsync().Result;
                    var token = JsonConvert.DeserializeObject<Guid>(result);
                }
        }


