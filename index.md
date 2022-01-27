<!-- CSS Stuff -->
<style type="text/css">
 * {text-align:center;}
 h2 {color:black;} 
 h4 {text-align: left;}
 ol, li {text-align: left;}
 table {text-align: left;}
 div {text-align: left; //display: inline-block;
 }
 .button {
  border: none;
  color: white;
  padding: 15px 15px;
  text-decoration: none; //display: inline-block;
  font-size: 16px; //margin: 2px 2px;
  cursor: pointer;
  background-color: #008CBA;
}
p {text-align: left;}
</style>


<!-- HTML Stuff -->
<h3> Risk Prediction for Septic Shock and/or Bacteremia Applied to Pediatric Oncology Patients Presenting with Fever and Neutropenia </h3>

<h4> Instructions: </h4>
<ol>
 <li>Check each risk factor that applies to your patient in the table.</li>
 <li>Click "Calculate Score" button to generate risk output.</li>
</ol> 
  
<table>
  <tr>
    <th>Predictor</th>
    <th>Points</th>
    <th>Check if true:</th>
  </tr>
  <tr>
    <td>Cancer Relapse</td>
    <th>11</th>
    <td><input type="checkbox" id="relapse" name="relapse" value="11"> </td>
  </tr>
 <tr>
    <td>Hematological Malignancy</td>
    <th>11</th>
    <td><input type="checkbox" id="hemat" name="hemat" value="11"> </td>
  </tr>
 <tr>
    <td>Hemoglobin <u><</u> 6.95 g/dL</td>
    <th>10</th>
    <td><input type="checkbox" id="hemo" name="hemo" value="10"> </td>
  </tr>
 <tr>
    <td>Platelets <u><</u> 79,000/μL</td>
    <th>9</th>
    <td><input type="checkbox" id="platelets" name="platelets" value="9"> </td>
  </tr>
  <tr>
    <td>Age (Years) > 9.79</td>
    <th>6</th>
    <td><input type="checkbox" id="age" name="age" value="6"> </td>
  </tr>
 <tr>
    <td>Absolute Monocyte Count <u><</u> 53</td>
    <th>6</th>
    <td><input type="checkbox" id="amc" name="amc" value="6"> </td>
  </tr>
 <tr>
    <td>Sex = Female</td>
    <th>5</th>
    <td><input type="checkbox" id="sex" name="sex" value="5"> </td>
  </tr>
 <tr>
    <td>Leukocyte Count <u><</u> 650</td>
    <th>4</th>
    <td><input type="checkbox" id="leuk" name="leuk" value="4"> </td>
  </tr>
 <tr>
    <td>Absolute Neutrophil Count <u><</u> 55</td>
    <th>2</th>
    <td><input type="checkbox" id="anc" name="anc" value="2"> </td>
  </tr>
 <!--
 <tr>
    <td>Days Since Chemotherapy Treatment > 10.5</td>
    <th>0</th>
    <td><input type="checkbox" id="days" name="days" value="0"> </td>
  </tr> 
-->
</table>

<div>  
 <button class="button" id="calcbutton"> Calculate Score </button>
 <p id="riskscore">Risk Score: N/A </p>
 <p> A Risk Score over 22 points indicates "High Risk."</p>
</div>

<!-- JavaScript Stuff -->
<script>
 
 function changeScore(){
  var hemat = parseFloat(document.getElementById("hemat").value) * document.getElementById("hemat").checked;
  var relapse = parseFloat(document.getElementById("relapse").value) * document.getElementById("relapse").checked;
  var hemo = parseFloat(document.getElementById("hemo").value) * document.getElementById("hemo").checked;
  var platelets = parseFloat(document.getElementById("platelets").value) * document.getElementById("platelets").checked;
  var age = parseFloat(document.getElementById("age").value) * document.getElementById("age").checked;
  var amc = parseFloat(document.getElementById("amc").value) * document.getElementById("amc").checked;
  var anc = parseFloat(document.getElementById("anc").value) * document.getElementById("anc").checked;
  var leuk = parseFloat(document.getElementById("leuk").value) * document.getElementById("leuk").checked;
  <!-- var days = parseFloat(document.getElementById("days").value) * document.getElementById("days").checked; -->
  var sex = parseFloat(document.getElementById("sex").value) * document.getElementById("sex").checked;
  <!-- let constant = -3.228; -->
  
  <!-- let risk = (1/(1 + Math.exp(-(hemat+relapse+hemo+platelets+gsf+age+amc+anc+leuk+days+sex+constant)))).toFixed(4); -->
 let risk = (hemat+relapse+hemo+platelets+age+amc+anc+leuk+sex).toFixed();
  var level;
  if(risk >= 23){
      var level = "    (High Risk)";
  }else {
      var level = "    (Low Risk)";
  }
  document.getElementById("riskscore").innerHTML = "Risk Score: " + risk + level;
 }
 
 document.getElementById("calcbutton").addEventListener("click", changeScore);
 
</script>
<!--
You can use the [editor on GitHub](https://github.com/jjschnur/FNmodel/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.


### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/jjschnur/FNmodel/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out. 
-->

