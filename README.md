# Hexadecimal para rgba();

Este é um simples bookmarklet, para converter cores no formato hexadecimal, para o formato RGBA.

Entre no link abaixo para testar

[Hexadecimal para rgba();](http://rayansostenes.github.io/bookmarklet-hexdecimal-to-rgb-color)

O código usado neste bookmarlet é o seguinte:

~~~~~js
  (function(){
      "use strict";
      var regex = /#([abcdef0-9]{1,2})([abcdef0-9]{1,2})([abcdef0-9]{1,2})/;
      var hexValue = prompt("Digite a cor em hexadecimal \nEx: #ffffff ou #fff");
      if (hexValue && (hexValue.length == 4 || hexValue.length == 7)) {
          hexValue = hexValue.toLowerCase().match(regex);
          if (hexValue[0].length == 4) {
  
              hexValue = hexValue.splice(1).map(function(v){
                  return ""+v+v;
              });
          }else{
              hexValue = hexValue.splice(1);
          }
  
          var rgbValue = hexValue.map(function(v){
              return parseInt(v,16);
          });
  
          alert(
              "A cor em rgba é \n\n" +
              "rbga("+rgbValue.join(",")+",1)"
          );
      }else{
          alert("A String que você digitou não é válida");
      }
  })();
~~~~
