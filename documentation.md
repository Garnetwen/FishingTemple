# Project 5
URL: http://159.223.162.238:6001/

---
## Process:
notes of notability in thinking about code: 
[Note Nov 22, 2024.pdf](https://github.com/user-attachments/files/18129891/Note.Nov.22.2024.pdf)

https://pickled-oyster-544.notion.site/FINAL-PROJECT-146e64dfb701805a9798c3d876a1ea4d?pvs=4
Dec 10-12: fixing the css:) Find out that it will be easier to put a big div in the body, and display flex the body.

   **creating my own json file**
I try to create my new database,because I couldn't find a free api about marine life.

   **pulling random fish and show it in the client side**
1. first I set up the server side to read the file, and set up the random pull function to get a random fish from the json file I created using a function getRandomFish() and send back to client side.
2. I create a fishing button, with function onclick(openPopup), where it use the fetch to get the random fish from the server side. And then I use the data.json to parsed data into the json format.**It is important to use two .then() function to wait for the parsed data to be converted into json** (unless it will always show undefine)
3. I assign the global variable localData as the parsedData (local data) so the global variable can be use in elsewhere without mess around other functions.

   **get 3 fish from the random pulling**
1. set a fishArray for storing fish data, set it as JSON.parse(localStorage.getItem("fishArray")) || []; so it will not return undefine as the first time.
2. the function closepopup() means the button collect it, once it is click it will set the localData (which is the random fish on the screen right now) into a localStorage data, and then transfer it into the json format again in order to push it into the fish Array. *[not sure if this step is necessary]*
3. set up a function for checking Fish array *function checkLocalData()*: if the length of array is larger or equal than 3, it means that it has more than three fishs in there, so the warning's innerHTML will be "cannnot put more than 3 fish". The second check point is that if we already got the same fish in our array, we will use array.some() to go over the array, as soon as it find the name of the fish in the array (fish.name) matched the the fish we are trying to collect (localData.name), we will not push the data and change the warning as "cannot be the same fish". The final check, which is the condition where we don't have 3 fish in our cabinet and the fish we are collecting is not the same as the ones in our cabinet, we push the localData into the fishArray.
   
   **after collected the fish, start counting down the time for fish status**
1. use a function to update fish status, and to update the specific fish status, I need to find the exact fish when I collected it. So i use the name of the fish as the pass in data (*localName = localData.name) and I set it the setTimeout function (*setTimeout(updateStaleStatus, 10000, localName);*),
2. after passing in the data, I use the array.find() to find the fish I collected. the return results will be the object (fish) with all attributes. Setting the fish status from "fresh" to "stale"
3. After change the fish status in the fish array, reset the whole array into the localStorage.
4. I do the same thing in the updateRottenStatus, the only difference is once fish get rotten, all fish are gone. so instead of array.find(), i use array array.forEach(), which it will infect all fish's status.
5. after the status change to rotten, another setTimeout function will use the localStorage.clear to delete all fish in the fishArray.

   **update Cabinet fish when it was collected from the fishing site**
1. wait for DOM content to be loaded and then start to append things.
2. One "mistake" I made is I set up the div so early in the ejs, the better option is to createElement in the script.js so I don't have to manually reload everything (I think that is the issue? from OH)
3. in the function *updateCabinet()*, I need to check for both fishArray[0] to see it the fish Array is empty, and whether image is null(not sure do i really need it). and then set the srcinfo as the Array[0].image as the src, and make it as the srce of the image.
4. Do that with the other 3 fishs and their status change too.

   **makeing a pop up for checking the fish status by clicking the fish img**
1. function I learnt from GPT is even.target.closest(), which allows me to  get the nearest Dom element, so it is the class,statusPopUp)
   
    

I learnt how to do the random pulling(same as json file):
https://stackoverflow.com/questions/43825595/how-to-get-a-random-record-from-my-nedb-database

trying to create a Pop up page 
learning youtube tutorial: 
https://www.youtube.com/watch?v=foB3Ke5LsNY&t=43s

1. realize i need another database for storing fish collected...
2. the closePopup function always not working, I use console.log and found there is no respond. I listen to GPT and she said there is a conflict between onclick attribute of the button, and it fixed the problem.
3. When I tried to view the object, it [Object HTMLelement], which I searched online, it requires the value.
4. showed https://stackoverflow.com/questions/15383765/javascript-viewing-object-htmlinputelement


css:
Trying to create audio:
https://gomakethings.com/how-to-play-a-sound-with-javascript/

video & screenshots process: 

https://github.com/user-attachments/assets/d4b21106-df13-4575-8e1f-c480f3c964ec
<img width="1962" alt="Screenshot 2024-12-09 at 10 47 36" src="https://github.com/user-attachments/assets/d0df575d-878f-42cd-be20-e364adf65a62" />
<img width="1050" alt="Screenshot 2024-12-07 at 19 27 26" src="https://github.com/user-attachments/assets/e114c241-3762-429c-a5ca-24c45daaf836" />
<img width="1163" alt="Screenshot 2024-12-07 at 19 24 22" src="https://github.com/user-attachments/assets/b79343a9-4474-46cd-ace3-1da94896eb1d" />


https://github.com/user-attachments/assets/1086d2a1-bc03-4145-980b-a83077bc7073



https://www.youtube.com/watch?v=T9GWHFDcELQ
---
