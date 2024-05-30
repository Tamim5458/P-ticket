document.getElementById('bus-ticket').addEventListener('click', function () {
    const busTicket = document.getElementById('ticket-section')
    const sectionOffsetTop = busTicket.offsetTop;
    window.scroll({
        top: sectionOffsetTop,
        behavior: 'smooth'
    });
})

let buttonInfoArray = [];

function clicked(btnId) {
    // Get the button element
    const btn = document.getElementById(btnId);

    const isSelected = buttonInfoArray.some(info => info.sit === btnId);

    // If the button has already been selected, prevent further actions
    if (isSelected) {
        return;
    }

    // Create an object with button information
    const buttonInfo = {
        sit: btnId,
        price: 550,
        class: 'Economoy'
    };

    // Push the object into the array
    buttonInfoArray.push(buttonInfo);
    btn.style.backgroundColor = '#1DD100';
    // Check if the array length is 4
    if (buttonInfoArray.length === 4) {
        // Display an alert
        alert('You have selected 4 buttons!');

        // Disable all buttons
        const buttons = document.querySelectorAll('.selectedbtn');
        buttons.forEach(button => {
            button.disabled = true;
        });
    }
    // Log the updated array
    const phone = check();
    generateSeatSelection(buttonInfoArray)
    totalsit(buttonInfoArray)
    totalPrice(buttonInfoArray)
    cuponButton(buttonInfoArray)
    nextButton(buttonInfoArray, phone)
    leftSit(buttonInfoArray)

}
function totalsit(buttonInfoArray) {
    const totalSit = document.getElementById('sit-number');
    totalSit.innerText = buttonInfoArray.length;
}
// sit left
function leftSit(buttonInfoArray) {
    const sitLeft = document.getElementById('seat-left');
    sitLeft.innerText = 40 - buttonInfoArray.length;
}
// coupon section calculation


function nextButton() {
    const phone = check();
    if (buttonInfoArray.length > 0 && phone != '') {
        const nextButton = document.getElementById('next')
        nextButton.disabled = false;

    }
}

function totalPrice(buttonInfoArray) {
    const totalSit = document.getElementById('total-price');
    totalSit.innerText = buttonInfoArray.length * 550;
}
function cuponButton(buttonInfoArray) {
    const cuponButton = document.getElementById('cupon-button');
    if (buttonInfoArray.length == 4) {
        cuponButton.disabled = false;
        cuponButton.style.backgroundColor = '#1DD100';
    }

}
function cuponButtondisable(buttonInfoArray) {
    const cuponButton = document.getElementById('cupon-button');
    if (buttonInfoArray.length == 4) {
        cuponButton.disabled = true;
        cuponButton.style.backgroundColor = '#1DD100';
    }

}
// cupon calculation
function cuponClaculationfor15(buttonInfoArray) {
    const totalSit = buttonInfoArray.length;
    const a = 550 * totalSit * .15;
    return a;
}
function cuponClaculationfor20(buttonInfoArray) {
    const totalSit = buttonInfoArray.length;
    const a = 550 * totalSit * .20;
    return a;
} 
// hidden discount price 
function discountHideUnhide(){
    const pp = document.getElementById('discount-price-hidden');
    pp.classList.remove('hidden');
}

//  Acction AFTER Click Apply button 
function click2(parameter) {

    const grandPrice = document.getElementById('grand-price');
    const discountPrice = document.getElementById('current-discount-price')
    const couponField = document.getElementById('cupon-filed').value;
    const price15 = cuponClaculationfor15(buttonInfoArray)
    const newpp = parseInt(price15)
    const price20 = cuponClaculationfor20(buttonInfoArray)
    const newpp2 = parseInt(price20)
    if (couponField === "NEW15") {
        discountPrice.innerText = newpp;
        grandPrice.innerText = 2200 - newpp;
        cuponButtondisable(buttonInfoArray);
        discountHideUnhide()
    }
    else if (couponField === "Couple 20") {
        discountPrice.innerText = newpp2;
        grandPrice.innerText = 2200 - newpp2;
        cuponButtondisable(buttonInfoArray);
        discountHideUnhide()

    }
    else {
        alert('Invalid Coupon Code');
    }
     
}
// Apply button end 


function generateSeatSelection(seatInfoArray) {
    const seatSelectionDiv = document.getElementById('sit');
    const seatInfoContainer = document.createElement('div');
    seatInfoContainer.classList.add('flex', 'flex-col', 'gap-6');

    // Seat info rows
    seatInfoArray.forEach(seat => {
        const seatRow = document.createElement('div');
        seatRow.classList.add('flex', 'justify-between', 'pl-8', 'pr-11', 'mt-4');
        seatRow.innerHTML = `
            <p class="text-base font-inter font-medium text-[#030712]">${seat.sit}</p>
            <p class="text-base font-inter font-medium text-[#030712]">${seat.class}</p>
            <p class="text-base font-inter font-medium text-[#030712]">${seat.price}</p>
        `;
        seatInfoContainer.appendChild(seatRow);
    });
     
    seatSelectionDiv.innerHTML = ''; 
    
    seatSelectionDiv.appendChild(seatInfoContainer);
}

function check() {
    const phone = document.getElementById('phone').value;
    return phone
}
// When click continued
function clickContinue(){
    location.reload();
}