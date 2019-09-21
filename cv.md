# Najmiddin Mirzoboev 


### Several ways to find me:
* My Email: najmiddin4242@gmail.com
* My phone number: +99897-390-42-42
* My Telegram [account](https://t.me/najeek)
* My Facebook [account](https://www.facebook.com/profile.php?id=100008073481703)
* My HeadHunter [resume](https://hh.uz/resume/f8774902ff06e93e110039ed1f464e4d474f64)

### Short summary:
**Purposefulness, constant self-development, sociability and sociability.
Analytical mindset, the ability to find a solution to complex problems.**

### My key skills:
- HTML5
- CSS3
  - SASS
  - SCSS
  - Bootstrap 3
  - Bootstrap 4
- JavaScript
  - EcmaScript 5   
  - EcmaScript 6   
  - Jquery
  - ReactJS
- Webpack
- NPM
- Node.Js   

### Code Examples:
*Following code is engine of weather app that I built by myself from scratch without any guides and courses:*
```javascript 
const list = document.querySelector('ul');
const results = document.querySelector('.result-cont')
const input = document.querySelector('input');
const searchBtn = document.querySelector('.search');
const locationBtn = document.querySelector('.location');
const errorWindow = document.querySelector('.error-window');

const displayErrMsg = (string) => {
    const template =  `<div class='error-container'>
                         <p class='error-text'>${string}</p>
                         <p class='close-btn' onclick="closeWin(this)"><i class="fas fa-times"></i></p>
                      </div>`
    errorWindow.insertAdjacentHTML("beforeend", template)
    errorWindow.style.display = 'flex';         
}

const convertTime = num => {
    const date = new Date(num * 1000);
    return date.toLocaleDateString();
}

const makeFirstBig = str => {
    return str.charAt(0).toUpperCase() + str.slice(1);
}

const closeWin = (elem) => {
    while(elem.className != 'error-window') {
        elem = elem.parentElement;
    }
     elem.innerHTML = '';
     elem.style.display = 'none';    
}

const addHtmlElems = (data) => {
    const days = data.list.filter(elem => elem.dt_txt.includes('12:00:00') ? true : false );
    const cityName = data.city.name;

    for(let i = 0; i < days.length; i++) {
      const forecast = days[i].main;
      const windSpeed = days[i].wind.speed;
      const weather = days[i].weather[0];
      const unit = `
      <section>
        <h2>${makeFirstBig(weather.description)} in ${cityName} at ${convertTime(days[i].dt)}</h2>
        <img src='http://openweathermap.org/img/w/${weather.icon}.png'>
        <p><i class="fas fa-temperature-low"></i> Temperature is ${parseInt(forecast.temp)}C</p>
        <p><i class="fas fa-bacon"> </i>Humidity is ${forecast.humidity}%</p>
        <p><i class="fas fa-wind"></i> Wind speed is ${windSpeed} mps</p>
      </section>`;
      results.insertAdjacentHTML('beforeend', unit);
  }
}

const addWeather = () => {
    if(input.value) {
     results.innerHTML = '';
     fetch(`${corsAccess}http://api.openweathermap.org/data/2.5/forecast?q=${input.value}&units=metric&&appid=${apiKey}`)
        .then(result => {return result.json()})
        .then(info =>  addHtmlElems(info))
        .catch(() => { 
            let cityNotFound = 'City is not found or you wrote incorrect one, please write existing city!'
            displayErrMsg(cityNotFound);
        })
    }else {
        let blankInput = 'Input box is empty, write your city or use GPS button to find city automatically '
        displayErrMsg(blankInput);
    }
    input.value = '';
} 

searchBtn.addEventListener('click', addWeather);
window.addEventListener('keypress', event =>  event.keyCode == 13 ? addWeather():'');

locationBtn.addEventListener('click', () => {
    results.innerHTML = '';
    navigator.geolocation.getCurrentPosition(position => {
            let lat = position.coords.latitude;
            let long = position.coords.longitude;   

            fetch(`${corsAccess}api.openweathermap.org/data/2.5/forecast?lat=${lat}&lon=${long}&units=metric&&appid=${apiKey}`)
                .then(result => result.json())
                .then(info => addHtmlElems(info)) 
    }, 
        error => {
            let errMsg = `Your error is:<br><span class='red'>${error.message}</span>.<br>Please try again :)`;
            displayErrMsg(errMsg);  
    });
    input.value = '';
})
```
You can use it [here](https://weather-4242.firebaseapp.com/)

### My working experience:
* telegram bot-maker intern (*6 months*)
* junior front-end intern - 'verstalshik' (*2 months*)
* testing tasks for reactjs developer position in outsource ukrainian company [beejee.ru](https://beejee.ru/)
* two websites for university module assessment

### My education:
* Certificate of Foundation Studies in University of Westminster
* Bachelors degree in Business Information Systems (*uncompleted*)
* Certificate of successful completion of **Full JavaScript Course** *Jonas Schmedtman*

### My english level:
*IELTS score 6.5





