# AlexaServerRfo

1. Necessário ter SSL 
2. Digital Ocean + Let's Encrypt: [https://goo.gl/kP4hpC](https://goo.gl/kP4hpC)
3. Necessário Node.js
```
$ sudo apt-get update
$ sudo apt-get install nodejs
$ sudo apt-get install npm
```
> Mais tarde vamos iniciar o servidor usando o Pm2 para o Node ficar
> rodando sozinho.
```
$ npm install pm2@latest -g
```
Instale o exemplo Alexa Server e adicione o exemplo de Skill.
	
	$ git clone git@github.com:ricardo7k/AlexaServerRfo.git
	$ cd AlexaServerRfo/
	$ npm install alexa-app-server
	$ npm init
	$ npm install request-promise
	$ git submodule add git@github.com:ricardo7k/AlexaSkillRfo.git apps/skill
	$ cd apps/skill
	$ npm init
	$ npm install alexa-app -save
	$ cd ../../
	$ pm2 start server.js

>Vamos para a Amazon. https://developer.amazon.com/

* Depois do Login, vá em Alexa, depois ```<Get Started>```

![alt tag](https://rfo.im/alexa/img/01.png)

* Clique em ```< Add a New Skill >```

![alt tag](https://rfo.im/alexa/img/02.png)

* Coloque um Name, e o invocation name (o que você irá pronunciar para a Alexa atender). Depois ```<Next>```

![alt tag](https://rfo.im/alexa/img/03.png)

* Insira um intents schema, Custom Slot Types (Add Slot) e Sample Utterances
```
{
  "intents": [
    {
    "intent": "GetNewIntent",
    "slots": [
        {
        "name": "variable",
        "type": "VARIABLE"
        }
      ]
    }
  ]
}
```
```
GetNewIntent for {variable}
GetNewIntent of {variable}
GetNewIntent clear {variable}
GetNewIntent {variable}
```

![alt tag](https://rfo.im/alexa/img/04.png)

```
< Next >
```
	
>Adicione a url onde ficará a skill instalada (Primeiro selecion https, North America)

![alt tag](https://rfo.im/alexa/img/05.png)

```
https://{url}/alexa/skill
```
>< Next >

Depois selcione: ```My development endpoint has a certificate from a trusted certificate authority```

![alt tag](https://rfo.im/alexa/img/06.png)

>< Next >

----------
### Vamos testar

![alt tag](https://rfo.im/alexa/img/07.png)

* Em Service Simulator
* Coloque o texto de invocation (super number)
* Ele responderá o que está na sua skill 
