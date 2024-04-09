

Backend dd-250




app.enableCors({

allowedHeaders: ["Content-Type", "Accept", "Authorization"],

origin: 'http://localhost:5002',

credentials: true,

methods: ["POST", "GET", "OPTIONS", "PATCH", "PUT", "DELETE"],

});





return this.jwtService.sign(JSON.parse(JSON.stringify(content)),



