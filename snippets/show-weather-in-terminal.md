## Display current weather in Terminal

To show the weather in your Terminal, use:

`curl wttr.in`


You can also specify a location using a forward-slash followed by placename:

eg.

`curl wttr.in/manchester`

or

`curl wttr.in/london`


You can compare two cities using this command:

`diff -Naur <(curl -s http://wttr.in/london ) <(curl -s http://wttr.in/manchester )`


Sources:  
https://askubuntu.com/questions/390329/weather-from-terminal  
https://github.com/chubin/wttr.in  
Developer: https://twitter.com/igor_chubin  
