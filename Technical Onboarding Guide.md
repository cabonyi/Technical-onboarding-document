

<img width="969" alt="Bildschirmfoto 2023-08-01 um 14 04 28" src="https://github.com/cabonyi/Technical-onboarding-document/assets/88483311/b9f1ccc4-29a8-44a9-ae24-2e2820a802e2">

# Technical Onboarding Guide
To alternatively view this file on Github, kindly visit this URL <https://github.com/cabonyi/Technical-onboarding-document/blob/main/Technical%20Onboarding%20Guide.md>

# Table of Contents

- [Purpose](#Purpose)
- [Introduction](#Introduction)
- [Import Schedule](#Import-Schedule)
- [Category Tree](#Category Tree)
- [XML Data Feed Ad Example](#XML-Data-Feed-Ad-Example)
- [Frequently Asked Questions](Frequently-Asked-Questions)
- [Feed Debugging and Validation](Feed-Debugging-and-Validation)
    
______
## Purpose
The purpose of this document is to assist Kleinanzeigen Advertising Partners during the Technical Onboarding phase.
______
## Introduction
Dear Valued Customer,

Congratulations on choosing Kleinanzeigen. We are thrilled to partner with you and assist you in showcasing your products to our extensive network of users. Our commitment to your success starts right here with this comprehensive onboarding guide.

As you embark on this exciting journey with us, we want to make your transition as smooth and efficient as possible. This guide is designed to walk you through the process of importing your product feeds into our Ad Server, so you can get your ads up and running quickly.
Here's what you need to know:

1. XML Feed: In the past, creating an XML feed was a customer responsibility. However, to streamline the process and ensure accuracy, our dedicated Technical Account Manager will now handle the creation of the XML feed for you. Details on how to proceed with this option are provided in the guide.

2. TSV (Tab-Separated Values) Feed: If you prefer, you can utilize TSV format to import your product feeds. This option offers flexibility and simplicity, and this guide includes step-by-step instructions to get you started.

3. API Connection (Beta Phase): For those interested in cutting-edge solutions, we are excited to offer an API connection. This option is currently in Beta testing phase, and we invite you to be part of this innovative integration. Please note that as this is a Beta feature, you'll have direct support from our technical team to ensure a seamless experience.
Our Customer Success team is always here to support you, and we encourage you to reach out with any questions or concerns. Your success is our success, and we are committed to providing you with the tools, resources, and personalized support you need to thrive on our platform.
______

## XML Data Feed Ad Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<ads xmlns:admarkt="http://admarkt.marktplaats.nl/schemas/1.0">
    <ad>
        <vendorId>42</vendorId>
        <title>Bally 1992 Adams Family</title>
        <description>Best pinball machine ever made</description>
        <categoryId>999</categoryId>
        <url>https://pinball.com/game/bally-adams-family/</url>
        <vanityUrl>https://pinball.com</vanityUrl>
        <price>875000</price>
        <originalPrice>875000</originalPrice>
        <priceType>FIXED_PRICE</priceType>
        <phoneNumber>16123456789</phoneNumber>
        <emailAdvertiser>true</emailAdvertiser>
        <sellerName>Pinball King</sellerName>
        <status>ACTIVE</status>
        <media>
            <image url="https://pinball.com/game/bally-adams-family/1.jpg"/>
        </media>
        <budget>
            <totalBudget>10000</totalBudget>
            <dailyBudget>1000</dailyBudget>
            <autobid>true</autobid>
        </budget>
        <shippingOptions>
            <shippingOption>
                <shippingType>PICKUP</shippingType>
                <location>1097DN</location>
            </shippingOption>
            <shippingOption>
                <shippingType>PICKUP</shippingType>
                <location>1055AB</location>
            </shippingOption>
            <shippingOption>
                <shippingType>SHIP</shippingType>
                <cost>695</cost>
                <time>2d-5d;</time>
            </shippingOption>
            <shippingOption>
                <shippingType>SHIP</shippingType>
                <cost>1195</cost>
                <time>1d-2d</time>
            </shippingOption>
        </shippingOptions>
        <attributes>
            <attribute>
                <attributeName>model</attributeName>
                <attributeValue>Adams Family</attributeValue>
            </attribute>
            <attribute>
                <attributeName>multiball</attributeName>
                <attributeValue>TRUE</attributeValue>
            </attribute>
            <attribute>
                <attributeName>screen size</attributeName>
                <attributeValue>32"</attributeValue>
            </attribute>
            <attribute>
                <attributeName>resolutions</attributeName>
                <attributeValue>1024x768:24dpi</attributeValue>
                <attributeValue>800x600:18dpi</attributeValue>
            </attribute>
        </attributes>
        <gtin>93845278905</gtin>
        <productType>Hobby &amp; Games &gt; Arcade Games &gt; Pinball Machines</productType>
        <googleProductCategory>Electronics &gt; Arcade Equipment &gt; Pinball Machines</googleProductCategory>
        <brand>Bally</brand>
        <condition>refurbished</condition>
        <energyEfficiencyClass>E</energyEfficiencyClass>
        <minEnergyEfficiencyClass>F</minEnergyEfficiencyClass>
        <maxEnergyEfficiencyClass>D</maxEnergyEfficiencyClass>
        <color>black/white/green</color>
        <gender>unisex</gender>
        <ageGroup>adult</ageGroup>
        <itemGroupId>BC23456</itemGroupId>
    </ad>
</ads>
```
______
## Import Types

-   XML : See below examples
-   TSV: [Download sample file here](https://github.com/cabonyi/Technical-onboarding-document/blob/fef352fa6fa06ae519c26314a030e6cea5a42dfd/iCAS%20TSV%20feed%20sample.xlsx)
-  API: TBD


## Feed Fields


A set of required and optional fields defined by a feed for XML file formats are listed below.

XML


|Field                      |Description                         |Restrictions      |Mandatory|
|:---------------------------|:------------------------------------|:-----------------:|:---------:|
|[vendor Id](#vendor-id)      |unique ad identifier                |max. 64 chars     |yes      |
|[price](#price)        |   product price in cents if applicable   |positive integer   |yes/no         |
|[title](#title)                |product title                       |see title         |yes      |
|[description](#description)    |product description                 |description       |yes      |
|[category id](#category_ids)   |category identifier                 |numeric, positive |yes      |
|[Url](#Url)                |product URL                         |max. 2048 chars   |yes      |
|[vanityUrl](#vanityUrl)    |displayed URL                       |max. 256 chars    |yes       |
|[price type](#price-type)  |sales model for product             |enum              |yes      |
|[status](#status)            |desired status (default ACTIVE)     |ACTIVE,PAUSED     |no       |
|[Attributes](#Attributes)    |collection of product attributes    |attributes        |no       |
|[budget](#budget)           |budget details                      |budget details    |no       |
|[shippingOptions](#shippingOptions)      |shipping options        |shipping & pick-up|no       |
|[MPN](#MPN)                        |Manufacturer Part Number (MPN)      |2-70 chars        |no       |
|[google product category](#google-product-category)    |google category for your product    |string            |no       |
|[product type](#product-type)               |customer product type               |max. 750 chars    |no       |
|[brand](#brand)                      |product brand name                  |max. 70 chars     |no       |
|[GTIN](#GTIN)                       |Global Trade Identification Number  |max. 50 chars     |no       |
|[item group id](#item-group-id )              |groups product variants in your     |max. 50 chars     |no       |
|[condition](#condition)                  |condition of product                |enum              |no       |
|[material](#material)                   |main product fabrics or materials   |max. 200 chars    |no       |
|[energy efficiency class](#energy-efficiency-class)    |energy efficiency class             |enum              |no       |
|[min energy efficiency class](#min-energy-efficiency-class)|minimal energy efficiency class     |enum              |no       |
|[max energy efficiency class](#max-energy-efficiency-class)|maximal energy efficiency class     |enum              |no       |
|[color](#color)                      |product colors                      |max. 100 chars    |no       |
|[gender](#gender)                     |gender product is designed for      |enum              |no       |
|[age group](#age-group)                  |age group product is intended for   |enum              |no       |
|[size](#size)                       |size information                    |enum              |no       |
|[unit pricing base measure](#unit-pricing-base-measure)  |denominator for product unit price  |string            |no       |
|[unit pricing measure](#unit-pricing-measure)       |measure and dimension of product    |string            |no       |
|original price             |original price before discount      |positive integer  |no       |
|media                      |product images                      |product images    |no       |
|phone number               |phone number                        |max. 32 chars     |no       |
|email advertiser           |allow emails to the seller          |true,false        |no       |
|seller name                |your company name                   |max. 60 chars     |no       |
|micro tip                  |tiny product highlight              |max. 18 chars     |no       |
______
### vendor Id 

The vendor id field is the _**unique identifier**_ of the ad. It is there to let us know, for consecutive imports, which ads are the same. This results is allowing us to track and update an existing ad with the same vendor id instead of creating a new ad. vendor id is mandatory and, unique for each ad in the feed.
```xml
        <vendorId>15839942</vendorId>
```
  Restrictions: Any non-empty string with a maximum length of 64 characters.
______
### title 

Use the title title field to clearly identify the product you are selling. The title is one of the most prominent parts of your ad or free listing. A specific and accurate title will help us show your product to the right customer.
```xml
        <title>Goedkope A-merk herenfietsen</title>
```
Restrictions: Any string, with minimum and maximum length determined by the category, with a maximum cap of 120 characters. See Categories. URLs are not allowed as part of the title.

______
### description
Use the description field to tell customers about the details of the product you are selling.

```xml      
        <description><![CDATA[
            <p><strong><u>De goedkoopste webshop</u></strong>
                <strong>voor tweedehands fietsen met garantie!
                Gratis en rijklaar thuisbezorgd!</strong>
            </p>
            <p><strong><br></strong>
            </p>
            <ul>
                <li><strong>Laagste prijsgarantie</strong></li>
                <li>Fietsen <strong>100% rijklaar</strong>
                gratis thuisbezorgd</li>
                <li><strong>Ruime voorraad</strong>, voor ieder wat wils</li>
                <li>Snelle <strong>customer service</strong>
                via Whatsapp, bellen en e-mail</li>
                <li>1 <strong>maand garantie</strong></li>
                <li>Aangesloten bij <strong>Webwinkelkeur</strong></li>
            </ul>
            <strong><br></strong>
            <p>Check dus snel onze website en vind de fiets die bij je past!<br>
            </p>
            <strong><br></strong>
            <p>WhatsApp, bel of mail ons voor verdere vragen.
            </p>]]>
        <description/> 
```
Restrictions: Any string, with minimum and maximum length determined by the category. See [Categories](http://ecg-icas.github.io/icas/doc/next/categories.html#categories). URLs are not allowed as part of the description. All HTML elements except for the ones below will be removed:

```
       <u> <em> <ul> <li> <p> <strong> <br>

```
______

### category id 
Use category id to place your product in the Categories tree.

Each product belongs to one and only one category.

```xml
     <categoryId>945</categoryId> 
```



Restrictions: An integer value from the category list. Must be an id of a leaf category with a non-zero parent id.
______
### status 
Use status to change the state of your ad.


Must be one of the following:

|Name| description  |
|---|---|
|ACTIVE|  The ad will be active (as long as there is budget for it) and it can be found on the marketplace. |
|  PAUSED |The ad will be paused, effectively not found on the marketplace.|


The provided (desired) status may differ from the resulting one, depending on the other conditions. For instance, budget may be depleted, or you may have too many active ads already in the category.
______
### Url 
Utilize the url to establish a connection to your product page from the advertisement. This represents an external URL, which will be displayed on the ad detail page or search result page.
```xml
        <url>https://www.bmw.de</url>
```
Restrictions: Must be a valid http(s) url.
______
### vanityUrl

Use vanity url to provide the text for the url link
```xml
        <vanityUrl>BMW</vanityUrl>
```
______
### PriceTypes
Use price type to define pricing model for your product.

```xml
        <priceType>FIXED_PRICE</priceType>
```

```xml
        <priceType>NOT_APPLICABLE</priceType>
```
Allowed Values: FIXED_PRICED, NOT_APPLICABLE
______
### price 
Use price to tell customers the price of the product you are selling. The meaning of the value depends on the price type.
Price should be in cent. In the example below, the price value is 15 EUR.
```xml
        <price>1500</price>
```
Restrictions: The maximum allowed price value is 10000000000 given in cents of the local market currency. (100.000.000,00 EUR / CAD / … )
______
### Images

You can provide multiple images for your product.

All images will be resized if necessary to a size of maximum 1024px height and 1024px width (preserving the aspect ratio) The system will download the images and, if they meet the requirements, store them on our servers in several sizes.

Use ```<media>``` tag for grouping your product images. ```<media>``` should contain from 0 to N ```<image>``` ordered elements, where the exact limit depends on the category in taxonomy. ```<image>``` elements must contain a complete URL link pointing to an image on a publicly available web server.

```xml
    <media>
    <image url="https://images.pexels.com/photos/62289/62289.jpeg"/>
    <image url="https://images.pexels.com/photos/47547/47547.jpeg"/>
    <media/>
```

The images will be presented in the provided order. The first image is shown in search results and acts as the main image on the item page.


Allowed image formats: JPEG, JPG, PNG, GIF*, BMP.

*Please note that GIFs are not recommended format as they are only 256 colors or less. Also, animated GIFs and PNGs are not supported.

______  
### Attributes
Use **attributes** field to provide additional information on your product in a structured way.

attributes tag contains collection of product User-Defined Attributes (category-dependent), that can be used to influence the ad relevance.

```xml
        <attributes>
            <attribute>
                <attributeName>color</attributeName>
                <attributeLocale>nl</attributeLocale>
                <attributeLabel>Kleur</attributeLabel>
                <attributeValue>Rood</attributeValue>
            </attribute>
            <attribute>
                <attributeName>color</attributeName>
                <attributeLocale>en</attributeLocale>
                <attributeLabel>Color</attributeLabel>
                <attributeValue>Red</attributeValue>
            </attribute>
            <attribute>
                <attributeName>Model</attributeName>
                <attributeValue>Slim</attributeValue>
                <attributeValue>Pro</attributeValue>
            </attribute>
        </attributes>
```

**attributes** tag contains collection of product [User-Defined Attributes](http://ecg-icas.github.io/icas/doc/next/attributes.html#user-defined-attributes) (category-dependent), that can be used to influence the ad relevance.
______

### shipping & pick-up
Provide the information on how your product can be delivered to customers.

You can provide multiple shipping/ pick-up options for each product. Each option can be described with the following information:

| Name   |      Description      |  Required |
|----------|:-------------:|------:|
| shippingType |  SHIP, PICKUP | Yes |
| time|    time it takes to deliver the product   |   No |
| location | pick up location of the product |    No |


_SHIP_ means the item can be delivered to the buyer in the provided time and for the provided cost. For shippingType ‘SHIP’ provide ‘cost’ in cents and ‘time’ in days. ‘location’ is ignored.

_PICKUP_ means the item can be picked up at the provided location For shippingType ‘PICKUP’ provide ‘location’. Both ‘cost’ and ‘time’ are ignored.

```xml
        <shippingOptions>
            <shippingOption>
                <shippingType>PICKUP</shippingType>
                <location>1097DN</location>
            </shippingOption>
        </shippingOptions>
```

Restrictions: Shipping options can be disabled/optional/mandatory for an ad. It is configured per category, see [Category Configuration](http://ecg-icas.github.io/icas/doc/next/categories.html#category-config-v2).

______
### MPN


Manufacturer Part Number (MPN), definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324482) guidelines.

```xml

        <mpn>AB12345R89TN6E</mpn>
```


Restrictions: String identifier max 70 characters long.
______
### google product category


Use this field to describe your product category in Google’s product taxonomy. See [Google Merchant Center](https://support.google.com/merchants/answer/6324436)

```xml

        <googleProductCategory>
            Apparel &amp; Accessories &gt; Clothing &gt; Dresses
        </googleProductCategory>
```


```xml
        <:googleProductCategory>2271</googleProductCategory>
```
Restrictions: Should be a valid category. You can provide it, either with identifier, or giving full category path.
______
### brand

Use the **brand** field to help customers identify your product. Brand definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324351) guidelines.

```xml
    <brand>iPhone</brand>
```

Restrictions: Do not exceed 70 characters limit for your text.

______
### product type


The **product type** field provides an opportunity for you to incorporate your unique product classification system into the dataset. Definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324406) guidelines.

```xml
        <productType>
        Home &gt; Women &gt; Dresses &gt; Maxi Dresses
       </productType>
```

Restrictions: Do not exceed 70 characters limit for your text.
______
### GTIN


GTIN (Your product’s Global Trade Item Number), definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324461) guidelines.


```xml
    <gtin>44320194113475</gtin>
```

Restrictions: String identifier max 50 chars.
______
### item group id


Use this field to group product variants in your product data. Item group id definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324507) guidelines.

```xml
    <itemGroupId>BC23456</itemGroupId>
```

Restrictions: Text max. length 50 characters.
______
### condition


Use this field to inform customers about the condition of your product. Condition definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324469) guidelines.

```xml
    <condition>used</condition>
```
Accepted values: _new_, _refurbished_, _used_
______
### material


**Material** field describes the main fabric or material that your product is made of. Material definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324410) guidelines.

```xml
    <material>Cotton/Silk</material>
```

Restrictions: Use human readable material names. Provide up to 3 materials. Separate materials with a slash (“/”) character when there are multiple. Do not exceed 200 characters limit for your text.
______
### energy efficiency class


Use this field to tell customers how your product rates on a given energy efficiency range. See [Google Merchant Center](https://support.google.com/merchants/answer/7562785)



Allowed values: _A+++_, _A++_, _A+_, _A++_, _B_, _C_, _B_, _E_, _F_, _G_

### min energy efficiency class


Used in combination with **max energy efficiency class** to describe the product energy efficiency label. Possible values defined in [energy efficiency class](#feed-energyefficiencyclass)

```xml
    <energyEfficiencyClass>A+</energyEfficiencyClass>
```
______
### max energy efficiency class


Used in combination with **min energy efficiency class** to describe the product energy efficiency label. Possible values defined in [energy efficiency class](#feed-energyefficiencyclass)

```xml
    <minEnergyEfficiencyClass>G</minEnergyEfficiencyClass>
```
______
### color 


Use **color** field to tell customers about the dominant colors of your product. Color definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324487) guidelines.

```xml
    <color>Black/Grey</color>
```
Restrictions: Use human readable color names. Provide up to 3 colors. Separate colors with / if more than one. Do not exceed 100 characters limit for your text.
______
### gender

Use **gender** field to describe the gender your product is designed for. Gender definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324479) guidelines.

```xml
    <gender>unisex</gender>
```
______
### age group


Use **age group** field to describe the age group your product is targeted at. Definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324463) guidelines.

```xml
    <ageGroup>adult</ageGroup>
```

Allowed values: _newborn_, _infant_, _toddler_, _kids_, _adult_
______
### size


Use **size** field to describe standardized size of your product. Size definition follows [Google Merchant Center](https://support.google.com/merchants/answer/6324492) guidelines.

```xml
    <unitPricingBaseMeasure>1kg</unitPricingBaseMeasure>
```

Restrictions: String identifier max 1-100 chars.
______
### unit pricing base measure
The denominator for product unit price. See [Google Merchant Center](https://support.google.com/merchants/answer/6324490). This field attribute tells the customer how the price of your product translates per unit.

```xml
    <unitPricingBaseMeasure>1kg</unitPricingBaseMeasure>
```

Restrictions: Value should be an integer number with unit.

Supported unit values:

*   **Weight**: _oz, lb, mg, g, kg_
    
*   **Volume**: _floz, pt, qt, gal, ml, cl, l, cbm_
    
*   **Length**: _in, ft, yd, cm, m_
    
*   **Area**: _sqft, sqm_
    
*   **Per unit**: _ct_
______    

### unit pricing measure

Defines the measure and dimension of the product. That value helps the customers to understand the exact price per unit for your product. Example 125ml, 100g. See [Google Merchant Center](https://support.google.com/merchants/answer/6324455).

```xml
    <unitPricingMeasure>15kg</unitPricingMeasure>
```
Restrictions: Value should be an integer number with a unit.

Supported unit values:

*   **Weight**: _oz, lb, mg, g, kg_
    
*   **Volume**: _floz, pt, qt, gal, ml, cl, l, cbm_
    
*   **Length**: _in, ft, yd, cm, m_
    
*   **Area**: _sqft, sqm_
    
*   **Per unit**: _ct_
______

## Frequently Asked Questions
Below are some common scenarios and questions with their explanations/answers.
<details>
  <summary>How to use TSV format?</summary>
    
    We introduced the TSV format in our system, to simplify the integration path. 
    Our customers commonly use spreadsheets to store and manipulate the data, 
    and “TSV export” is a standard option for the majority of spreadsheet programs.

The three important things to remember for successful integration:

    1.There are some column names, that we will look for, and expect to find in your TSV feed.
    2.Multiline fields need to be escaped with double quotes, or all the line breaks changed to \n.
    3.Some complex fields, like shipping & pick-up or attributes must follow the specified encoding conventions.

</details>

<details>
  <summary>What are the newly added fields</summary>

Those fields are considered a ‘widely adopted market standard’, required, or recommended for advertising on many other channels: 
  - [MPN](mpn)
  - [google product category](#google-product-category)
  - [brand](#brand)
  - [product type](#product-type)
  - [GTIN](#gtin)
  - [item group id](#item-group-id)
  - [condition](#condition)
  - [material](#material)
  - [energy efficiency class](#energy-efficiency-class)
  - [min energy efficiency class](#min-energy-efficiency-class)
  - [max energy efficiency class](#max-energy-efficiency-class)
  - [color](#color)
  - [gender](#gender)
  - [age group](#age-group)
  - [size](#size)
  - [unit pricing base measure](#unit-pricing-base-measure)
  - [unit pricing measure](#unit-pricing-measure)
</details>

<details>
  <summary>What happens if my feed file cannot be fetched</summary>
    
    When a feed file cannot be fetched, nothing will change on the user’s ads. It’s as if the import didn’t happen.
    Since the file represents the desired list of ads to be live, we won’t do anything if we can’t get the file - 
    we cannot read a change in the desired situation.

</details>

<details>
  <summary>I have updated my feed images, and after the successful import there is no change.</summary>

    If you’re changing the images without changing the URLs, the changes may not be picked up, in case the rest of the ad is also unchanged.
    We suggest adding a bogus parameter to the image URL to force a re-processing of the ad and its images. 
    Make sure to not change this for every feed import, but only when you require images to be re-processed.
</details>

<details>
  <summary>What happens if my feed file cannot be fetched</summary>

    If the fetched XML file does not validate against the XSD there will be no changes to your ads.
    Existing ads will remain unchanged and no new ads will be created.
</details>

<details>
  <summary>What happens when my XML does not validate against XSD</summary>

    If the fetched XML file does not validate against the XSD there will be no changes to your ads. 
    Existing ads will remain unchanged and no new ads will be created.
</details>

<details>
  <summary>Do I have to insert a price if I am business model do not support prices</summary>

    For service providers (for e.g in the Job category), combination of the following tags ``` <price>0</price> ``` 
    and ` <priceType>NOT_APPLICABLE</priceType>` can be used to achieve the same purpose.
</details>

<details>
  <summary> Do I need to add a Price?</summary>

    Yes, Price is mandatory. If you are using ‘FIXED_PRICE’ as your priceType then the value must be greater than ‘0’.

    For customers importing Jobs or Services using ‘0’  for price is suggested
</details>


<details>
  <summary> Do I need to include a budget?</summary>

    Yes, Price is mandatory. If you are using ‘FIXED_PRICE’ as your priceType then the value must be greater than ‘0’.
    For customers importing Jobs or Services using ‘0’  for price is suggested

 **Sample Budget XML:**
    
      <budget>
    
         <cpc>50</cpc>
    
         <dailyBudget>2500</dailyBudget>
    
         <totalBudget>50000</totalBudget>

   </budget>

    Based on the above configuration, this Ad will no longer be displayed when the total budget exceeds 50000 Cents (€500)
    or the daily budget exceeds 2500 Cents (€25).
    
    The Daily Budget for Ads is reset at midnight, where the Total Budget persits as long as the item is included in the feed.
    Daily Budget is an optional field and can be left blank. 
    When setting the Daily Budget via the feed, the value must be 10 Cents or greater.
    

    **There is also the ‘Feed Daily' budget which controls the limit for the entire feed. 
    This budget is configured by an eBK Admin and must be discussed with the Business Development prior to the feed activation.

</details>

<details>
  <summary> What is a vanityUrl? Do we need it?</summary>

    The vanityUrl is a mandatory field. This field is displayed in the Ad and should be ‘YourCompanyName.com’
</details>


<details>
  <summary> How can I display Ads which offer Free shipping? </summary>

```xml
     <attributes>

            <attribute>

                <attributeName>shipment_cost_visible</attributeName>

                <attributeLabel>Versandkosten anzeigen</attributeLabel>

                <attributeLocale>de_DE</attributeLocale>

                <attributeValue>true</attributeValue>

            </attribute>

            <attribute>

                <attributeName>shipment_cost_desc</attributeName>

                <attributeLabel>Versandkosten</attributeLabel>

                <attributeLocale>de_DE</attributeLocale>

                <attributeValue>Versandkostenfrei</attributeValue>

            </attribute>

        </attributes>
```
</details>.


______
### Feed Debugging and Validation

All data feeds must be validated before importing to the EBK platform. The command line script below can be used in any terminal to identify errors.

When an error is reached, the script will terminate and output the error to the console.

    When the file passes the validation process, the script will output to the console:
    
    ‘fileName.xml validates’

**Validation Script:**

    xmllint --nonet --nowarning --noout --encode "UTF-8" --dropdtd --noent fileName.xml --schema Admarkt.xsd
    
    -Replace filename.xml with your XML file name.



______
<img width="969" alt="Bildschirmfoto 2023-08-01 um 14 04 28" src="https://github.com/cabonyi/Technical-onboarding-document/assets/88483311/b9f1ccc4-29a8-44a9-ae24-2e2820a802e2">

# Kleinanzeigen's Category Tree

| L1 - CATEGORY NAME      | L2 - SUB CATEGORY                | CATEGORY ID | Attributes                                                                                                                                                                                                                                  |
| ----------------------- | -------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Auto_Rad_Boot           |                                  |             |                                                                                                                                                                                                                                             |
|                         | Anhaenger_Nutzfahrzeuge          | 276         | Agrarfahrzeuge, Anhänger, Baumaschinen, Busse, LKW, Sattelzugmaschinen & Auflieger, Stapler, Nutzfahrzeugteile & Zubehör, Weitere Nutzfahrzeuge & Anhänger                                                                                  |
|                         | Autos                            | 216         |                                                                                                                                                                                                                                             |
|                         | Autoteile_Reifen                 | 223         | Auto Hifi & Navigation, Ersatz- & Reparaturteile, Reifen & Felgen, Tuning & Styling, Werkzeug, Weitere Autoteile                                                                                                                            |
|                         | Boote_Bootszubehoer              | 211         | Motorboote, Segelboote, Kleinboote, Schlauchboote, Jetski, Bootstrailer, Bootsliegeplätze, Bootszubehör, Weitere Boote                                                                                                                      |
|                         | Fahrraeder                       | 217         |                                                                                                                                                                                                                                             |
|                         | Motorraeder_Roller               | 305         | Mofas & Mopeds, Motorräder, Quads, Motorroller & Scooter                                                                                                                                                                                    |
|                         | Motorraeder_Roller_Teile         | 306         | Ersatz- & Reparaturteile, Reifen & Felgen, Motorradbekleidung                                                                                                                                                                               |
|                         | Reparaturen_Dienstleistungen     | 280         |                                                                                                                                                                                                                                             |
|                         | Wohnwagen_Mobile                 | 220         | Alkoven, Integrierter, Kastenwagen, Teilintegrierter, Wohnwagen, Weitere Wohnwagen & -mobile                                                                                                                                                |
|                         | Sonstiges                        | 241         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Eintrittskarten_Tickets |                                  |             |                                                                                                                                                                                                                                             |
|                         | Comedy_Kabarett                  | 254         |                                                                                                                                                                                                                                             |
|                         | Kinder                           | 252         |                                                                                                                                                                                                                                             |
|                         | Klassik_Kultur                   | 251         |                                                                                                                                                                                                                                             |
|                         | Konzerte                         | 255         |                                                                                                                                                                                                                                             |
|                         | Sport                            | 257         |                                                                                                                                                                                                                                             |
|                         | Bahn_OEPNV                       | 286         |                                                                                                                                                                                                                                             |
|                         | Gutscheine                       | 287         |                                                                                                                                                                                                                                             |
|                         | Sonstige                         | 256         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Familie_Kind_Baby       |                                  |             |                                                                                                                                                                                                                                             |
|                         | Altenpflege                      | 236         |                                                                                                                                                                                                                                             |
|                         | Baby_Kinderkleidung              | 22          | Hosen & Jeans, Kleider & Röcke, Shirts & Tops, Hemden, Jacken & Mäntel, Pullover & Strickjacken, Wäsche, Sportbekleidung, Bademode, Accessoires, Kleidungspakete, Weitere Baby- & Kinderkleidung                                            |
|                         | Baby_Kinderschuhe                | 19          | Ballerinas, Halb- & Schnürschuhe, Hausschuhe, Sandalen, Outdoor & Wanderschuhe, Sneaker & Sportschuhe, Stiefel & Stiefeletten, Badeschuhe, Weitere Schuhe                                                                                   |
|                         | Babyausstattung                  | 258         |                                                                                                                                                                                                                                             |
|                         | Babyschalen_Kindersitze          | 21          |                                                                                                                                                                                                                                             |
|                         | Babysitter_Kinderbetreuung       | 237         |                                                                                                                                                                                                                                             |
|                         | Kinderwagen_Buggys               | 25          |                                                                                                                                                                                                                                             |
|                         | Kinderzimmermoebel               | 20          | Betten & Wiegen, Hochstühle & Laufställe, Schränke & Kommoden, Wickeltische & Zubehör, Wippen & Schaukeln, Weitere Kinderzimmermöbel                                                                                                        |
|                         | Spielzeug                        | 23          | Action- & Spielfiguren, Babyspielzeug, Barbie & Co, Dreirad & Co, Gesellschaftsspiele, Holzspielzeug, LEGO & Duplo, Lernspielzeug, Playmobil, Puppen, Spielzeugautos, Spielzeug für draußen, Stofftiere, Weiteres Spielzeug                 |
|                         | Sonstiges                        | 18          |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Freizeit_Nachbarschaft  |                                  |             |                                                                                                                                                                                                                                             |
|                         | Esoterik_Spirituelles            | 232         |                                                                                                                                                                                                                                             |
|                         | Essen_Trinken                    | 248         |                                                                                                                                                                                                                                             |
|                         | Freizeitaktivitaeten             | 187         |                                                                                                                                                                                                                                             |
|                         | Handarbeit_Basteln_Kunsthandwerk | 282         |                                                                                                                                                                                                                                             |
|                         | Kuenstler_Musiker                | 191         |                                                                                                                                                                                                                                             |
|                         | Kunst                            | 240         |                                                                                                                                                                                                                                             |
|                         | Modellbau                        | 249         |                                                                                                                                                                                                                                             |
|                         | Reise_Eventservices              | 233         |                                                                                                                                                                                                                                             |
|                         | Sammeln                          | 234         | Ansichts- & Postkarten, Autogramme, Bierkrüge & -gläser, Briefmarken, Comics, Flaggen, Münzen, Porzellan, Puppen & Puppenzubehör, Sammelbilder & Sticker, Sammelkartenspiele, Überraschungseier, Werbeartikel, Weiteres Sammeln             |
|                         | Sport_Camping                    | 230         | Ballsport, Camping & Outdoor, Fitness, Radsport, Tanzen & Laufen, Wassersport, Wintersport, Weiteres Sport & Camping                                                                                                                        |
|                         | Troedel_kistenweise              | 250         |                                                                                                                                                                                                                                             |
|                         | Verloren_Gefunden                | 189         |                                                                                                                                                                                                                                             |
|                         | Sonstiges                        | 242         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Haus_Garten             |                                  |             |                                                                                                                                                                                                                                             |
|                         | Badezimmer                       | 91          |                                                                                                                                                                                                                                             |
|                         | Bueromoebel                      | 93          |                                                                                                                                                                                                                                             |
|                         | Dekoration                       | 246         | Bilder & Poster, Kerzen & Kerzenhalter, Spiegel, Vasen, Weitere Dekoration                                                                                                                                                                  |
|                         | Dienstleistungen_Haus_Garten     | 239         | Bau & Handwerk, Garten- & Landschaftsbau, Haushaltshilfe, Reinigungsservice, Reparaturen, Wohnungsauflösungen, Weitere Dienstleistungen Haus & Garten                                                                                       |
|                         | Garten_Pflanzen                  | 89          | Blumentöpfe, Dekoration, Gartengeräte, Gartenmöbel, Pflanzen, Weiteres Gartenzubehör & Pflanzen                                                                                                                                             |
|                         | Heimtextilien                    | 90          |                                                                                                                                                                                                                                             |
|                         | Heimwerken                       | 84          |                                                                                                                                                                                                                                             |
|                         | Kueche_Esszimmer                 | 86          | Besteck, Geschirr, Gläser, Kleingeräte, Küchenschränke, Stühle, Tische, Weiteres Küche & Esszimmer                                                                                                                                          |
|                         | Lampen_Licht                     | 82          |                                                                                                                                                                                                                                             |
|                         | Schlafzimmer                     | 81          | Betten, Lattenroste, Matratzen, Nachttische, Schränke, Weiteres Schlafzimmer                                                                                                                                                                |
|                         | Wohnzimmer                       | 88          | Regale, Schränke & Schrankwände, Sitzmöbel, Sofas & Sitzgarnituren, Tische, TV & Phonomöbel, Weiteres Wohnzimmer                                                                                                                            |
|                         | Sonstiges                        | 87          |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Haustiere               |                                  |             |                                                                                                                                                                                                                                             |
|                         | Fische                           | 138         | Aquariumfische, Barsche, Diskusfische, Garnelen & Krebse, Koi, Schnecken, Wasserpflanzen, Welse, Weitere Fische                                                                                                                             |
|                         | Hunde                            | 134         | Mischlinge, Beagle, Bernhardiner, Border Collie, Boxer, Cocker Spaniel, Collie, Dackel, Dalmatiner, Dobermann, Dogge, Golden Retriever, Husky, Jack Russell Terrier, Labrador, Malteser, Pudel, Schäferhunde, Spitz, Terrier, Weitere Hunde |
|                         | Katzen                           | 136         | Britisch Kurzhaar, Hauskatze, Maine Coon, Perser, Siam, Weitere Katzen                                                                                                                                                                      |
|                         | Kleintiere                       | 132         | Hamster, Hasen & Kaninchen, Mäuse & Ratten, Meerschweinchen, Weitere Kleintiere                                                                                                                                                             |
|                         | Pferde                           | 139         | Großpferde, Kleinpferde & Ponys                                                                                                                                                                                                             |
|                         | Reptilien                        | 244         | Schlangen, Echsen, Spinnen, Weitere Reptilien                                                                                                                                                                                               |
|                         | Tierbetreuung_Training           | 133         |                                                                                                                                                                                                                                             |
|                         | Vermisste_Tiere                  | 283         | Entlaufen, Gefunden                                                                                                                                                                                                                         |
|                         | Vogel                            | 243         |                                                                                                                                                                                                                                             |
|                         | Sonstige                         | 131         |                                                                                                                                                                                                                                             |
|                         | zubehoer                         | 313         | Fische, Hunde, Katzen, Kleintiere, Pferde, Reptilien, Vögel, Weiteres Zubehör Haustiere                                                                                                                                                     |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Immobilien              |                                  |             |                                                                                                                                                                                                                                             |
|                         | Auf_Zeit_WG                      | 199         |                                                                                                                                                                                                                                             |
|                         | Ferienwohnung_Ferienhaus         | 275         | Kaufen, Mieten                                                                                                                                                                                                                              |
|                         | Garage_Lagerraum                 | 197         | Kaufen, Mieten                                                                                                                                                                                                                              |
|                         | Gewerbeimmobilien                | 277         | Kaufen, Mieten                                                                                                                                                                                                                              |
|                         | Grundstuecke_Garten              | 207         |                                                                                                                                                                                                                                             |
|                         | Haus_kaufen                      | 208         |                                                                                                                                                                                                                                             |
|                         | Haus_mieten                      | 205         |                                                                                                                                                                                                                                             |
|                         | Umzug_Transport                  | 238         |                                                                                                                                                                                                                                             |
|                         | Wohnung_kaufen                   | 196         |                                                                                                                                                                                                                                             |
|                         | Wohnung_mieten                   | 203         |                                                                                                                                                                                                                                             |
|                         | Sonstiges                        | 198         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Jobs                    |                                  |             |                                                                                                                                                                                                                                             |
|                         | Ausbildung                       | 118         |                                                                                                                                                                                                                                             |
|                         | Bau_Handwerk_Produktion          | 111         | Bauhelfer, Dachdecker, Elektriker, Fliesenleger, Maler, Maurer, Produktionshelfer, Schlosser, Tischler, Weitere Berufe                                                                                                                      |
|                         | Bueroarbeit_Verwaltung           | 114         | Buchhalter, Bürokauffrau/-mann, Sachbearbeiter/-in, Sekretärin, Weitere Berufe                                                                                                                                                              |
|                         | Gastronomie_Tourismus            | 110         | Barkeeper, Hotelfachfrau/-mann, Kellner/-in, Koch/Köchin, Küchenhilfe, Servicekraft, Zimmermädchen, Weitere Berufe                                                                                                                          |
|                         | Heimarbeit_Mini_Nebenjobs        | 107         |                                                                                                                                                                                                                                             |
|                         | Kundenservice_Callcenter         | 105         |                                                                                                                                                                                                                                             |
|                         | Praktika                         | 125         |                                                                                                                                                                                                                                             |
|                         | Sozialer_Sektor_Pflege           | 123         | Altenpfleger/-in, Arzthelferin, Erzieher/-in, Krankenschwester/ Krankenpfleger, Physiotherapeut/-in, Weitere Berufe                                                                                                                         |
|                         | Transport_Logistik_Verkehr       | 247         | Kraftfahrer, Kurierfahrer, Lagerhelfer, Staplerfahrer, Weitere Berufe                                                                                                                                                                       |
|                         | Vertrieb_Einkauf_Verkauf         | 117         | Buchhalter/-in, Immobilienmakler, Kaufmann/-frau, Verkäufer/-in, Weitere Berufe                                                                                                                                                             |
|                         | Sonstige_Berufe                  | 109         | Designer/Grafiker, Friseur/-in, Haushaltshilfe, Hausmeister, Reinigungskraft, Weitere Berufe                                                                                                                                                |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Mode_Beauty             |                                  |             |                                                                                                                                                                                                                                             |
|                         | Accessoires_Schmuck              | 156         | Mützen, Schals & Handschuhe, Schmuck, Sonnenbrillen, Taschen & Rucksäcke, Uhren, Weitere Accessoires & Schmuck                                                                                                                              |
|                         | Beauty_Gesundheit                | 224         | Make-Up & Gesichtspflege, Haarpflege, Körperpflege, Hand- & Nagelpflege, Gesundheit, Weiteres Beauty & Gesundheit                                                                                                                           |
|                         | Kleidung_Damen                   | 154         | Hemden & Blusen, Hosen, Jacken & Mäntel, Pullover, Röcke & Kleider, Shirts & Tops, Umstandsmode, Weitere Damenbekleidung                                                                                                                    |
|                         | Kleidung_Herren                  | 160         | Hemden, Hosen, Jacken & Mäntel, Pullover, Shirts, Weitere Herrenbekleidung                                                                                                                                                                  |
|                         | Schuhe_Damen                     | 159         | Ballerinas, Halb- & Schnürschuhe, Hausschuhe, Outdoor & Wanderschuhe, Pumps & High Heels, Sandalen, Sneaker & Sportschuhe, Stiefel & Stiefeletten, Weitere Schuhe                                                                           |
|                         | Schuhe_Herren                    | 158         | Halb- & Schnürschuhe, Hausschuhe, Sandalen, Sneaker & Sportschuhe, Stiefel & Stiefeletten, Outdoor & Wanderschuhe, Weitere Schuhe                                                                                                           |
|                         | Sonstiges                        | 155         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Multimedia_Elektronik   |                                  |             |                                                                                                                                                                                                                                             |
|                         | Audio_Hifi                       | 172         | CD Player, Lautsprecher & Kopfhörer, MP3 Player, Radio & Receiver, Stereoanlagen, Weiteres Audio & Hifi                                                                                                                                     |
|                         | Dienstleistungen_EDV             | 226         |                                                                                                                                                                                                                                             |
|                         | Foto                             | 245         | Kamera, Objektiv, Zubehör, Kamera & Zubehör, Weiteres Foto                                                                                                                                                                                  |
|                         | Handy_Telekom                    | 173         | Apple, HTC, LG, Motorola, Nokia, Samsung, Siemens, Sony, Faxgeräte, Telefone, Weitere Handys & Telefone                                                                                                                                     |
|                         | Haushaltsgeraete                 | 176         | Haushaltskleingeräte, Herde & Backöfen, Kaffee- & Espressomaschinen, Kühlschränke & Gefriergeräte, Spülmaschinen, Staubsauger, Waschmaschinen & Trockner, Weitere Haushaltsgeräte                                                           |
|                         | Konsolen                         | 279         | Pocket Konsolen, PlayStation, Xbox, Wii, Weitere Konsolen                                                                                                                                                                                   |
|                         | Notebooks                        | 278         |                                                                                                                                                                                                                                             |
|                         | PC_Videospiele                   | 227         | DS, Nintendo Spiele, PlayStation Spiele, Xbox Spiele, Wii Spiele, PC Spiele, Weitere Videospiele                                                                                                                                            |
|                         | PC_Zubehoer_Software             | 225         | Drucker & Scanner, Festplatten & Laufwerke, Gehäuse, Grafikkarten, Kabel & Adapter, Mainboards, Monitore, Multimedia, Netzwerk & Modem, Prozessoren / CPUs, Speicher, Software, Tastatur & Maus, Weiteres PC-Zubehör                        |
|                         | PCs                              | 228         |                                                                                                                                                                                                                                             |
|                         | TV_Video                         | 175         | DVD-Player & Recorder, Fernseher, TV-Receiver, Weitere TV & Video                                                                                                                                                                           |
|                         | Tablets_reader                   | 285         | iPad, Kindle, Samsung Tablets, Weitere Tablets & Reader                                                                                                                                                                                     |
|                         | Sonstiges                        | 168         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Musik_Film_Buecher      |                                  |             |                                                                                                                                                                                                                                             |
|                         | Buecher_Zeitschriften            | 76          | Antiquarische Bücher, Kinderbücher, Krimis & Thriller, Kunst & Kultur, Sachbücher, Science Fiction, Unterhaltungsliteratur, Zeitgenössische Literatur & Klassiker, Zeitschriften, Weitere Bücher & Zeitschriften                            |
|                         | Buero_Schreibwaren               | 281         |                                                                                                                                                                                                                                             |
|                         | Comics                           | 284         |                                                                                                                                                                                                                                             |
|                         | Fachbuecher_Schule_Studium       | 77          |                                                                                                                                                                                                                                             |
|                         | Film_DVD                         | 79          |                                                                                                                                                                                                                                             |
|                         | Musik_CDs                        | 78          |                                                                                                                                                                                                                                             |
|                         | Musikinstrumente                 | 74          |                                                                                                                                                                                                                                             |
|                         | Sonstiges                        | 75          |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Unterricht_Kurse        |                                  |             |                                                                                                                                                                                                                                             |
|                         | Beauty & Gesundheit              | 269         |                                                                                                                                                                                                                                             |
|                         | Computerkurse                    | 260         |                                                                                                                                                                                                                                             |
|                         | Esoterik_Spirituelles            | 265         |                                                                                                                                                                                                                                             |
|                         | Kochen_Backen                    | 263         |                                                                                                                                                                                                                                             |
|                         | Kunst_Gestaltung                 | 264         |                                                                                                                                                                                                                                             |
|                         | Musik_Gesang                     | 262         |                                                                                                                                                                                                                                             |
|                         | Nachhilfe                        | 268         |                                                                                                                                                                                                                                             |
|                         | Sportkurse                       | 261         |                                                                                                                                                                                                                                             |
|                         | Sprachkurse                      | 271         |                                                                                                                                                                                                                                             |
|                         | Tanzkurse                        | 267         |                                                                                                                                                                                                                                             |
|                         | Weiterbildung                    | 266         |                                                                                                                                                                                                                                             |
|                         | Sonstige                         | 270         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Zu_verschenken_Tauschen |                                  |             |                                                                                                                                                                                                                                             |
|                         | Tauschen                         | 273         |                                                                                                                                                                                                                                             |
|                         | Verleihen                        | 274         |                                                                                                                                                                                                                                             |
|                         | Zu_verschenken                   | 192         |                                                                                                                                                                                                                                             |
|                         |                                  |             |                                                                                                                                                                                                                                             |
| Dienstleistungen        |                                  |             |                                                                                                                                                                                                                                             |
|                         | Altenpflege                      | 288         |                                                                                                                                                                                                                                             |
|                         | Auto_Rad_Boot                    | 289         |                                                                                                                                                                                                                                             |
|                         | Babysitter_Kinderbetreuung       | 290         |                                                                                                                                                                                                                                             |
|                         | Haus_Garten                      | 291         | Bau & Handwerk, Garten- & Landschaftsbau, Haushaltshilfe, Reinigungsservice, Reparaturen, Wohnungsauflösungen, Weitere Dienstleistungen Haus & Garten                                                                                       |
|                         | Kuenstler_Musiker                | 292         |                                                                                                                                                                                                                                             |
|                         | Multimedia_Elektronik            | 293         |                                                                                                                                                                                                                                             |
|                         | Reise_Event                      | 294         |                                                                                                                                                                                                                                             |
|                         | Tierbetreuung_Training           | 295         |                                                                                                                                                                                                                                             |
|                         | Umzug_Transport                  | 296         |                                                                                                                                                                                                                                             |
|                         | Sonstige                         | 298         |                                                                                                                                                                                                                                             |



      
