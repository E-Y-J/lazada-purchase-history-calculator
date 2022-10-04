# Lazada Purchase History Calculator
hehe

## STEPS

Below are the steps you have to follow, bare with me kasi manual calculation to di ko mapagana yung API eh HAHAHAH katamad

### 1. Login your Lazada account on the Lazada Website (must be browser)

### 2. Click the your name at the top right and then click my orders

![step2](https://user-images.githubusercontent.com/47263311/193888402-4f08aa02-5f42-470b-a5fa-f8de4609cb22.png)
	
### 3. Once the order page loads, please click the dropdown select beside "show" and click "All Orders"

![step3](https://user-images.githubusercontent.com/47263311/193888422-a0a5aa3e-a5ca-40e8-9cd1-d11799d8614a.png)

### 4. Right Click anywhere on the webpage and click on develop tools and inspect

![step4](https://user-images.githubusercontent.com/47263311/193888457-4a485f5a-abdb-44e1-96dd-d3dd59f94b56.png)

### 5. Click on the console tab of the developer tools thing (see image)

![setp 5](https://user-images.githubusercontent.com/47263311/193888469-29026b76-dd48-4bf5-aa4e-ab73eebfc632.png)

### 6. Paste the code and press enter (see image)

![step6](https://user-images.githubusercontent.com/47263311/193888487-1530ebfd-767d-404f-8c4a-6d71ddebefce.png)

# Code

```javascript
var pages = document.getElementsByClassName("next-pagination-list")[0].children.length;
var total = 0.0;

function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

for(let i = 0; i < pages; i++){
    if(i !== 0) document.getElementsByClassName("next-pagination-list")[0].children[i].click();
    await sleep(5000);
    let pageOrders = document.getElementsByClassName("orders")[0].children.length;
    for(let j = 0; j < pageOrders; j++){
        var element = document.getElementsByClassName("orders")[0].children[j].innerText;
        let receivedString = element.indexOf("Received");
        let deliveredString = element.indexOf("Delivered");
        if(receivedString !== -1) {
            let newString = element.substring(element.lastIndexOf("₱")+1, element.lastIndexOf("\n"));
            total += parseFloat(newString.replace(/,/g, ''));
        }
        if(deliveredString !== -1) {
            let newString = element.substring(element.lastIndexOf("₱")+1, element.lastIndexOf("\n"));
            total += parseFloat(newString.replace(/,/g, ''));
        }
    }
}

console.log("final: " + total);
```
