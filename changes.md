# Visual to the UI (CSS, visual elements)
   ## Focus Visible:
  ![focusvisibleissue](https://cloud.githubusercontent.com/assets/17002788/25632808/eca5eb68-2f29-11e7-8af1-0133bd0e3f66.PNG)

Ensure to make focus visible on link with keyboard and tab events on      Individuals & families, small business, Login.
### How to Fix:
```
a:focus, a:hover {
    color: #2a6496;
    }
```
## Contrast:  
Ensure to provide good contrast ratio for Remove Button and on selection and mouse hover. Also the ESPONOL button on the top:
![contrast-issue3](https://cloud.githubusercontent.com/assets/17002788/25634108/43a47b32-2f2e-11e7-9cf7-56ad372496ff.PNG)

 ![contrast-issue](https://cloud.githubusercontent.com/assets/17002788/25634158/6910ea64-2f2e-11e7-956b-0913d0f975f4.PNG)

### Contrast Ratio: 4.53:1
* Normal Text: Sample
AA: Pass
AAA: Fail
* Large Text: Sample
AA: Pass
AAA: Pass


![contrast-issue2](https://cloud.githubusercontent.com/assets/17002788/25634512/c9eed3f4-2f2f-11e7-8573-cf3110fe49bf.PNG)


### Contrast Ratio: 1.16:1
* Normal Text: Sample
AA: Fail
AAA: Fail
* Large Text: Sample
 AA: Fail
 AAA: Fail


 
### How to Fix: 
  Make sure make high contrast ratio combination of background and foreground.  



# Technical changes: HTML, JS, ARIA attributes, other
 ## Ensure to use correct ARIA attribute:
```
 <input aria-describedby="search-hint" class="form-control ng-touched ng-not-empty ng-dirty ng-valid-parse ng-valid ng-valid-required" id="search-input" placeholder="Enter ONE doctor, facility, or prescription drug at a time" type="text" required="" ng-model="providers.inboundSearchTerm">
```

ID should refer to elements which exist in the DOM
The aria-describedby property may be used to attach descriptive information to one or more elements through the use of an id reference list. The id reference list contains one or more unique element ids.
### How to Fix: 
```
<label for="search-input"><span class="sr-only"> SEARCH</span></label> 
<input aria-describedby="search-hint" class="form-control ng-touched ng-not-empty ng-dirty ng-valid-parse ng-valid ng-valid-required" id="search-input" placeholder="Enter ONE doctor, facility, or prescription drug at a time" type="text" required="" ng-model="providers.inboundSearchTerm">
<p id="search-hint ">Serach here your doctor, facility, or prescription drug </p>
```
Also can provide aria-label: aria-label is more helpful to support assistive technology. It is generally best practice to provide aria label as many screen reader like NVDA not read out placeholder text. 
```
<input  Aria-label=” Enter ONE doctor, facility, or prescription drug at a time” aria-describedby="search-hint" class="form-control ng-touched ng-not-empty ng-dirty ng-valid-parse ng-valid ng-valid-required" id="search-input" placeholder="Enter ONE doctor, facility, or prescription drug at a time" type="text" required="" ng-model="providers.inboundSearchTerm">
<p id="search-hint ">Serach here your doctor, facility, or prescription drug </p> 
```

Ensure to use correct ARIA attribute:
```
<a class="previous transparent u-font-size-deci qa-previous-doctors" aria-describedby="" href="" ng-click="getPage(previousPage)" ng-if="previousPage">
<span aria-hidden="true">←</span> Previous<span class="visuallyhidden ng-binding">page of results for this group()</span></a>
```

### How to Fix: 
Use aria-label=”Description about “ or delete aria-describedby=""  and use only already present span element. 
Ensure content updates define focus updates appropriately   [WCAG 2 .0: ( 2.4.3)] 
It is important for developer to notify assistive technologies that page content has updated when a page reload does not occur. In many single page application, assistive technology users might get confused or frustrated if he is not get inform with respective changes. 
On this page user should get notify search result, selection result and number of results and category of results. 
1.	Developer should use aria-live, role="alert" aria-atomic="true" to notify updates.

2.	Developer should maintain focus as per update result on appropriate element.
After clicking on more button focus should maintain on top section of result. 

 ![previouse-more](https://cloud.githubusercontent.com/assets/17002788/25634559/ee399442-2f2f-11e7-8d51-135711f2630a.PNG)

```
<a aria-describedby="" aria-controls="hcapp-providerResult" class="next transparent u-font-size-deci qa-next-doctors" href="" ng-if="nextPage" ng-click="getPage(nextPage)">
More <span aria-hidden="true">→</span> <span class="visuallyhidden">page of results for this group</span>
</a>
```
### How to fix
  Examples of code:
              Using .focus() method in javascript:
```
focusMethod = function getFocus() {           document.getElementById("myTextField").focus();
}
<input type="text" id="myTextField" value="Text field.">
<p></p>
<button type="button" onclick="focusMethod()">Click me to focus on the text field!</button>

```

# Content

WCAG 2.0 Chechlist  for  https://www.healthcare.gov/see-plans/#/search
1.3.1 Info and Relationships
1.4.3 Contrast (Minimum)
2.4.3 Focus Order
2.4.7 Focus Visible
3.3.2 Labels or Instructions
4.1.1 Parsing (HTML)

## Recommendation
1.	Provide info-Relationship using labels and aria attribute.
2.	Create live updates for assistive technology.
3.	Manage focus on update results. 
4.	Improve contrast level. 
