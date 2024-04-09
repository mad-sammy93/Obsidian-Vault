app.enableCors({

allowedHeaders: ["Content-Type", "Accept", "Authorization"],

origin: 'http://localhost:5002',

credentials: true,

methods: ["POST", "GET", "OPTIONS", "PATCH", "PUT", "DELETE"],

});