---
title: "Calculator"
bg: '#63BD2F'
color: white
fa-icon: usd
---

# How much could you save?

Enter in some basic information about your income and your property value below to calculate how much money you might save by applying for the tax credit.

<div align="center">
    <form name="calculator">
        <input type="textfield" name="income" value="30000">  
        &nbsp; &nbsp; &nbsp;        
        <input type="textfield" name="taxcost" value="250000">    
        &nbsp;        
        <input type="button" value="Estimate" onClick="calculations()">
        <br>
        Your Household Income
        &nbsp; &nbsp; &nbsp;
        Approximate Property Value
         &nbsp; &nbsp; &nbsp; &nbsp;  &nbsp;  &nbsp;  &nbsp; &nbsp; &nbsp;        
        <br>
        <br>
        <br>
        <input type="textfield" name="taxlimit" value="1680">
        &nbsp; &nbsp; &nbsp;        
        <input type="textfield" name="taxsavings" value="3820">     
        &nbsp; &nbsp;    &nbsp;   
        <input type="reset" value="Reset">
        <br>
        Expected Tax Limit
         &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        Expected Savings
         &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
    </form>
</div>

<script>
function calculations() {
    taxrate = 0.022

    startingval = eval(document.calculator.income.value)
    if (startingval > 8000) {
        calcedval = 0
        startingval -= 8000
    } else {
        startingval = 0
        calcedval = 0
    }
    
    if (startingval > 4000) {
        startingval -= 4000
        calcedval += .04*4000
    } else {
        calcedval += .04 * startingval
        startingval = 0
    }
    
    if (startingval > 4000) {
        startingval -= 4000
        calcedval += .065*4000
    } else {
        calcedval += .065*startingval
        startingval = 0
    }
    
    calcedval += .09*startingval
    startingval = 0
    
    document.calculator.taxlimit.value = calcedval
    
    savings = eval(document.calculator.taxcost.value)*taxrate - calcedval
    if (savings < 0) {
        savings = 0
    }
    
    document.calculator.taxsavings.value = savings
}
</script>