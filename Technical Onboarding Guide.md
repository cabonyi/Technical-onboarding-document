<img width="969" alt="Bildschirmfoto 2023-08-01 um 14 04 28" src="https://github.com/cabonyi/Technical-onboarding-document/assets/88483311/b9f1ccc4-29a8-44a9-ae24-2e2820a802e2">


# Table of Contents

- [Purpose](#Purpose)
- [Introduction](#Introduction)
- [Import Schedule](#Import-Schedule)
- Category Tree
- XML Data Feed Ad Example
- Feed Debugging and Validation
- FAQ
    - Price
    - Budget
    - URL’s	
    - Shipping Option
______
## Purpose
The purpose of this document is to assist Kleinanzeigen Advertising Partners during the Technical Onboarding phase.
______
## Introduction
Kleinanzeigen’s 1st Party Advertising platform provides our partners the ability to publish relevant Advertising inventory on <http://Kleinanzeigen.de>.
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
|[description](description)    |product description                 |description       |yes      |
|[category id](category_ids)   |category identifier                 |numeric, positive |yes      |
|[Url](Url)                |product URL                         |max. 2048 chars   |yes      |
|[vanityUrl](vanityUrl)    |displayed URL                       |max. 256 chars    |yes       |
|[price type](price-type)  |sales model for product             |enum              |yes      |
|[status](status)            |desired status (default ACTIVE)     |ACTIVE,PAUSED     |no       |
|original price             |original price before discount      |positive integer  |no       |
|media                      |product images                      |product images    |no       |
|[Attributes](Attributes)    |collection of product attributes    |attributes        |no       |
|[budget](budget)           |budget details                      |budget details    |no       |
|[shippingOptions](shippingOptions)      |shipping options        |shipping & pick-up|no       |
|phone number               |phone number                        |max. 32 chars     |no       |
|email advertiser           |allow emails to the seller          |true,false        |no       |
|seller name                |your company name                   |max. 60 chars     |no       |
|micro tip                  |tiny product highlight              |max. 18 chars     |no       |
|[MPN](MPN)                        |Manufacturer Part Number (MPN)      |2-70 chars        |no       |
|[google product category](google-product-category)    |google category for your product    |string            |no       |
|[product type](product-type)               |customer product type               |max. 750 chars    |no       |
|[brand](brand)                      |product brand name                  |max. 70 chars     |no       |
|[GTIN](GTIN)                       |Global Trade Identification Number  |max. 50 chars     |no       |
|[item group id](item-group-id )              |groups product variants in your     |max. 50 chars     |no       |
|[condition](condition)                  |condition of product                |enum              |no       |
|[material](material)                   |main product fabrics or materials   |max. 200 chars    |no       |
|[energy efficiency class](energy-efficiency-class)    |energy efficiency class             |enum              |no       |
|[min energy efficiency class](min-energy-efficiency-class)|minimal energy efficiency class     |enum              |no       |
|[max energy efficiency class](max-energy-efficiency-class)|maximal energy efficiency class     |enum              |no       |
|[color](color)                      |product colors                      |max. 100 chars    |no       |
|[gender](gender)                     |gender product is designed for      |enum              |no       |
|[age group](age-group)                  |age group product is intended for   |enum              |no       |
|[size](size)                       |size information                    |enum              |no       |
|[unit pricing base measure](unit-pricing-base-measure)  |denominator for product unit price  |string            |no       |
|[unit pricing measure](unit-pricing-measure)       |measure and dimension of product    |string            |no       |
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
<details>
  <summary>Example in XML</summary>

  
```xml
     <categoryId>945</categoryId> 
```
</details>

<details>
  <summary>Example in TSV</summary>

| Category iD  |
|:----------:|
| 945 |

</details>.



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
Allowed Values: FIXED_PRICED
______
### price 
Use price to tell customers the price of the product you are selling. The meaning of the value depends on the price type.
```xml
        <price>1500</price>
```
Restrictions: The maximum allowed price value is 10000000000 given in cents of the local market currency. (100.000.000,00 EUR / CAD / … )
______
### Images {#images}

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
