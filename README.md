# Snake---Jogo-da-Cobrinha
jogo da cobrinha
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="cobrinha.css">
    <title>Jogo Cobrinha - DIO</title>
</head>
<h1> Jogo da Cobrinha - DIO</h1>
<body>


    <canvas id="stage" width="500" height="500"></canvas>
    <script type="text/javascript">
     
        
        var stage = document.getElementById("stage");
        var ctx = stage.getContext('2d');
        document.addEventListener("keydown" , keyPush);

        setInterval(game,60);
        const vel=.5;
        var vx=vy=0;
        var px=10;
        var py=15;
        var tp=20;
        var qp=20;
        var ax=ay=15;

        var trail = [];
        tail =5;

        function game (){

            px += vx;
            py += vy;

            if (px < 0 ) { px = qp-1; }

            if (px > qp-1 ){px=0; }
            
            if (py < 0){py = qp-1; }

            if (py > qp-1) {py = 0; }
        
            
        ctx.fillStyle = "#09F";//AZUL
        ctx.fillRect(0, 0, stage.width , stage.height);

        ctx.fillStyle="green";
        ctx.fillRect( ax*tp, ay*tp, tp, tp);

        ctx.fillStyle = "red";
        for (var i = 0 ; i < trail.length; i++) {
            ctx.fillRect(trail[i] .x * tp , trail[i].y * tp, tp, tp, tp);
            if (trail[i].x == px && trail[i].y == py) 
            
            { vx = vy = 0;  }      
        }

        trail.push({x:px,y:py})
        while (trail.length > tail ){
            trail.shift();
                                   }

        if (ax==px && ay==py){
            tail++;
            ax = Math.floor(Math.random()*qp);
            ay = Math.floor(Math.random()*qp);
                           }
        }

        function keyPush(event) {
            switch (event.keyCode) {

                case 37: vx = -vel;
                vy = 0;
                break;
                case 38: vx = 0;
                vy = -vel;
                break;
                case 39: vx = vel;
                vy = 0;
                break;
                case 40: vx = 0;
                vy = vel;
                break;
            
             }
        }    
   
    </script>

</body>
</html>
