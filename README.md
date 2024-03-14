# Optimizing-Our-App
Namste React Episode 9
Custom Hooks
  useRestaurantMenu
  useOnlineStatus
  
Lazy Loading
  Suspense

Single Responsibility Principal 
>Keeps your component light and maintainable
>break into small small component
>very modular  


Custom Hooks
>> Hooks are just normal function
>creating custom hook is not mandatory thing
 but its a good thing boz that will make code readable,usable
>we can create our own custom hooks 
>Hooks are like utility function whether its a custom hooks or it is given by library useState useEffect

Now we are taking RestaurantMenu Component and abstract its API in custom hooks 
and then call into aur RestaurantMenu component so it become more light and readable.

 
**SO here RestaurantMenu have two major task which is 
     I> fetching The Data
	 II> Displaying The Fetched Data to the UI

>So we can reduce the task of fetching data and it only concern about displaying the  RestaurantMenu component Data
>so for fetching The Data we are creating the Custom hooks 

>here we are abstracting the fetching data logic to the custom hooks
>So here we are creating a custom hooks useRestaurantMenu and gets resInfo into that 

>we have to fetch data from this resInfo and put into our custome hook
>so RestaurantMenu does not have to worries about how to fetch the data 
>RestaurantMenu does not have to mange its own state 

>TO achieve this we have to create our own custom hooks 

<b>How to create own Custom hooks </b>
>to fetch the data of RestaurantMenu and and give it back to RestaurantMenu 
>the best place to create this helper function is in utils 
> create New file in the utils file with keyword "use"
>"useRestaurantMenu"
>The name of the file is exactly same name of that Hook
>also always start name of the file in lower case with use keyword
> SO that react know that its a custom hook as it starting with small "use"

>when ever you are writing hook think in this term only first of all try to see the CONTRACT
 what it is getting as the Input and what it is getting as the output
 
what is the contract of this hook
> it gets a resID now it has to fetch the data and return the restro Information back to where the hook is call from
<useRestaurantMenu/>

created  custom hooks

>Before writing the hooks you need know wht is input/output of the hook

<!-------------------------------------------------------------------->

Is it mandatory to use use(useOnlineStatus) in custom hooks 
> it is not mandatory to use but it is recommended to use before the name 
> linters will give error if don't write use

**useOnlineStatus**
>so we have to make a custom hook which can tell the user that you are online or Offline 

>for this we have to use online event listener

window.addEventListener("online", (event) => {});
ononline = (event) => {};

> to add this event linters in our useOnlineStatus component
> so this will render for once for this we will use useEffect
> we will useEffect along with empty dependency array
>so that whatever is written inside this useEffect it will executed once 
> and we will put our event listener once and now the job of this
  EventListener to track the status of internet 
  
  44:00
<!-------------------------------------------------------------------->

How to optimise the app 
>Chunking/Code Splitting/Lazy Loading/Dynamic Building
>these all are the different name of same thing


>>Smaller builder of js file and the process is know as 
>Make your app smaller 
>>Chunking/Code Splitting/Lazy Loading/Dynamic Building  
>we call Lazy Loading why because when our app load initially our app homepage will load
 it will not load code for the Grocery Component( component where we use lazy loading ) 
 only when I go to the Grocery page then it will load that page 
 this is also know as On Demand Loading
 
<b>How to do Lazy Loading</b>

>we will not import that component first 
>we will get Grocery in our App by using Lazy
>Lazy is a function which is given by React Package 
>it comes as a named import
>Now we will Lazy Load it by using callback function and then write import
>this import is basically a function which is not smiler to the one we use to import
>this function takes the path of the Grocery where it is come from

     import React, { lazy } from "react";
	 
     const Grocery = lazy(() => import("./components/Grocery"));  

>Now when you see the file in network then you see that there is two JS file one is index and another 
 is Grocery.js
>Grocery has its own bundle and our main bundle is separate
>in case the page is not loading and throwing error then it will be handled by suspance 


** Suspense **
> it is a component which is come from react    
> we can use lazy loading when the App become bigger
   to distribute the component into different Chunks 
   which help in reducing the loading time of the App
   
> to reduce the bundle size we reduce this code spiting we 
  do this lazy loading Chunking/Code Splitting/Lazy Loading/Dynamic Building
    
>this is alos know as dynamic import   
>by using this all the code will not come until you not call that page 