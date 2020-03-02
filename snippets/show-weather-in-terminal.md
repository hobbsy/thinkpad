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

## More options

`sudo apt install finger`  
`finger london@graph.no`

example output from this:

```
               -= Meteogram for united_kingdom/england/london =-                
 'C                                                                   Rain
  9   =--^^^=--                                                       
  8^^^         =--                                                    
  7               ---                                                 
  6                                                                   
  5                  ---                                          ^^^ 
  4                     ------                                        
  3                           ---                              ^^^    
  2                              ---------------------                
  1                                                   ------=--       
  0                                                                   
   _12_13_14_15_16 17 18 19 20 21 22 23 00 01 02 03 04 05 06_07_08_09 Hour
 
    NW NW NW NW  W  W SW SW SW SW SW SW SW SW SW SW SW SW SW SW SW SW Wind dir.
     5  5  6  6  6  4  3  4  4  4  4  4  4  4  4  4  4  4  4  4  5  5 Wind(mps)

Legend left axis:   - Sunny   ^ Scattered   = Clouded   =V= Thunder   # Fog
Legend right axis:  | Rain    ! Sleet       * Snow
[Try finger @graph.no for more info.]
```
