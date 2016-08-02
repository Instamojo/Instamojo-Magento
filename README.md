Instamojo-Magento  
====
----
This module allows us to use [Instamojo](https://www.instamojo.com) as Payment Gateway with Magento.


### Installation
---

####Let's assume for the rest of this article that your website URL is **http://www.example.com**.

Open Magento Connect Manager from the admin backend, usually its url is **http://www.example.com/downloader/**.

If that didn't work then go to the admin backend and then **System -> Magento Connect -> Magento Connect Manager.** This page may prompt for username and password again for security reasons.

![enter image description here](http://i.imgur.com/DlbocCD.png)


After entering username and password you will see the page shown below:

![enter image description here](http://i.imgur.com/z9Lu6WQ.png)

Here first go to **settings**:

![enter image description here](http://i.imgur.com/Sq0vNfF.png)

And change the value of **Magento Connect Channel Protocol** from "**Https**" to "**Http**" and click on **Save Settings**.

![enter image description here](http://i.imgur.com/cYmViRw.png)


Now go back to the previous page by clicking on **Extensions** and enter **http://connect20.magentocommerce.com/community/Instamojo_Imojo** in **Paste extension key to install** under **Install New Extensions**:

![enter image description here](http://i.imgur.com/SNOAo6K.png) 

Now click on **Install** and after that Magento will show you a package by the name of **Instamojo_Imojo** with some version number. Now click on "**Proceed**" to install the extension(**Note:** Always choose the latest stable version in case it is displaying multiple options)

![enter image description here](http://i.imgur.com/7hMGDVB.png)

Once the installation is done **Instamojo_Imojo** will show up in the list of extensions:

![enter image description here](http://i.imgur.com/f07fD4T.png)

Now that we have installed the extension it's time to configure this extension.

### Configuration

To configure the extension in admin panel go to **System -> Configuration -> Payment Methods**.

![enter image description here](http://i.imgur.com/yEqa9ww.png) 	

![enter image description here](http://i.imgur.com/pL1vz0C.png)

Here you will see a list of Payment methods already installed along with **Instamojo Checkout**.

![enter image description here](http://i.imgur.com/bPl0Vcz.png)

Now make sure **Enabled** is set to **Yes** if you want to use this extension during checkout, and change the values of **Payment Action** and **New order status** to **Authorize and Capture** and **Processing** respectively.

### Creating a Product
----
In this section we will learn how to create a product along with how to get the required values for `Payment Link` and `Custom Field` .

- Create a product by clicking on **Add a Product** on your Instamojo dashboard and choose the category **Other**.

  Set the price to Rs. 10 and enable **"Pay what you want"**.  Under **Title** and **Description**, you may enter something that describes your business and the nature of the products being sold.

  Under **Advanced settings** of the same product there's a field **Custom Redirection URL**. Here if your website's url is **http://www.example.com** then use **http://www.example.com/index.php/imojo/payment/response/** as **Custom Redirection URL**.

![enter image description here](http://i.imgur.com/eNtCxCX.png)

 Click on **Add Product to Store** to save the product.
 
- Copy the product URL and paste this in **Payment Link** field. URL's format is usually: **https://www.instamojo.com/username/slug/**.
- On the product page go to **More options** and click on **Custom Fields**. Create a custom field called **Order ID** and mark it as **required**. Click on **Add Custom Field** to save this custom field. 

 ![enter image description here](http://i.imgur.com/qhCMtJc.png)

 After the custom field has been created **Existing Custom Fields** section will appear. Copy the name shown under **Field ID** column, its format is **Field_xxxx**, where **xxxx** are some numbers(Note that this is case sensitive!). In this example the value is **Field_6473**.

![enter image description here](http://i.imgur.com/XRnsxwz.png)

Enter this value in the **Custom field** field of the Instamojo module configuration page in Magento.

#### Auth
----
Go the [Instamojo developers](https://www.instamojo.com/developers/) page, if your are not logged in already then login first and then you'll see the value of `API Key`,  `Auth token`,  `Private salt` there on the bottom left side of the page. Copy these values and paste them in their respective fields in  **Instamojo Checkout** configuration.


At the end the Configuration will look something like this:

![enter image description here](http://i.imgur.com/lauHc3I.png)

Click on **Save Config** to save these settings. Now we are ready to use Instamojo as payment gateway.

---

During checkout users can choose the option "**Pay using Instamojo**".

![enter image description here](http://i.imgur.com/SiqAU3S.png)

---

#### **Note:** Don't forget to replace all the instances of **www.example.com** with your website's URL.
