//console.log("Welcome to fiori on cloud development");
 const express = require('express');
 var app = express();

 //to use express.static middleware so that any new file inside webapp we dont have to serve again with app.get coomand
 // like below for json, html
app.use("/",express.static("webapp/"))
 this.vendors=[
    {
        "companyName":"ABC",
        "Country":"USA"
    },
    {
        "companyName":"DEF",
        "Country":"AUS"
    },
    {
        "companyName":"GHI",
        "Country":"INDIA"
    },
    {
        "companyName":"GHI",
        "Country":"ENG"
    }]

    //to serve json
app.get("/vendors",(req,res)=>{
    res.json(this.vendors);
})
app.get("/index.html",(req,res)=>{

    //file inside parent directory serve, we can whole bbc site
res.sendFile(__dirname + "/webapp/index.html");
})
 app.get("/",(req,res)=>{
    res.send("Welcome to my Website");
 })

 //html page serve
 app.get("/home",function(req,res){
        res.send("<label>What's your name?</label><input><br><button>Submit</button>");
 })
 console.log("Your server started on http://localhost:3001");

 // because CF has 8080 ports reserved for apps deployed via cloud cf push
 const portno = process.env.PORT || 3001;
 app.listen(portno);

 //cf push <app-name> and manifest.yml should not have - name : <app-name>. if it will be there, you will get
 // error like name not found