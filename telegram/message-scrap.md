This script will work in browser. This will help you scrape all the text messages from particular channel or chat. 

```
let preCount=0
let sameCount=0
let messages = []
let scrollToTop = () => {
	let myDiv = document.querySelector('.im_history_message_wrap');
	myDiv.scrollIntoView();
	let divs = document.querySelectorAll('.im_message_text');
	if (preCount == divs.length) {
        sameCount+=1;
    } else{
        sameCount=0;
        preCount = divs.length;
    }
    let timeOut;
    if(sameCount!=5) {
        timeOut = setTimeout(scrollToTop, 3000);
    } else {
        clearTimeout(timeOut);
        timeOut=0;
        let messagesDivs = document.querySelectorAll('.im_message_text')
        for (const message of messagesDivs) {
            messages.push(message.innerText)
        }
        console.log("Finished!")
    }
};

scrollToTop()
//wait for Finished! log then run copy command
copy(messages)
```