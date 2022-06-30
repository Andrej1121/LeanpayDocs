## Namestitev in konfiguracija

Na spodnji povezavi si lahko prenesete zadnji Leanpay vtičnik skupaj z navodili.

<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Add icon library -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
  <div style="text-align:center;">
		<a href="https://storage.googleapis.com/stoplight-resources/Download/Leanpay-Magento-1.X.zip" download>
		<button class="btn" style="width:30%"><i class="fa fa-download"></i> Prenos vtičnika</button>
  </div>
</body>
</html>


## Plugin Installation Guide

- Download Files
- Upload the files into Magento Root
- Flush the Cache!

![](https://storage.googleapis.com/stoplight-resources/Magento1/cache_management1.png)
![](https://storage.googleapis.com/stoplight-resources/Magento1/cache_management2.png)

- Logout and Login back to Admin
- Navigate to System

![](https://storage.googleapis.com/stoplight-resources/Magento1/system.png)

- Configuration

![](https://storage.googleapis.com/stoplight-resources/Magento1/system2.png)

- Sales category and select Payment Methods button

![](https://storage.googleapis.com/stoplight-resources/Magento1/payment_methods.png)

- Click on Leanpay.com tab and set Enable on "Yes"

![](https://storage.googleapis.com/stoplight-resources/Magento1/leanpaycomtab.png)

## Configuration - Admin

- After successful extension installation, you can see its configurations in:
  - System -> Configuration -> Sales -> Payment Methods , Leanpay.com tab ![](https://storage.googleapis.com/stoplight-resources/Magento1/leanpaycomtab.png)

<table>
  <tbody>
    <tr>
      <th>Configuration Name</th>
      <th>Option/Field Type</th>
      <th>Description</th>
      <th>View</th>
    </tr>
    <tr>
      <td>Enable Extension</td>
      <td>
        <ul>
          <li>Enable</li>
          <li>*Disable</li>
        </ul>
      </td>
      <td>Enables or disables the extension. Disable is set by the default</td>
      <td>Website</td>
    </tr>
    <tr>
      <td>Title</td>
      <td>Input (26 characters is the limit)</td>
      <td>Admin can enter the title of the payment method. It appears in the checkout. Default value is “Leanpay”.</td>
      <td>Store View</td>
    </tr>
    <tr>
      <td>Description</td>
      <td>Textarea (110 characters is the limit)</td>
      <td>Admin can add the description that appears in the checkout if Leanpay payment method is selected.</td>
      <td>Store View</td>
    </tr>
    <tr>
      <td>Base Currency Rate</td>
      <td>String</td>
      <td>Informative message that states current exchange rate. If the exchange rate is not set for base currency, the error will be displayed. By hovering on the tooltip, admin will see the helper message on how to set the currency exchange rate</td>
      <td>Website</td>
    </tr>
    <tr>
      <td>Environment</td>
      <td>
        <ul>
          <li>Demo*</li>
          <li>*Production</li>
        </ul>
      </td>
      <td>Allows to switch the environments between Demo and Production. Demo is set by default</td>
      <td>Website</td>
    </tr>
    <tr>
      <td>API Key</td>
      <td>Input</td>
      <td>Merchant’s API Key has to be entered here.</td>
      <td>Website</td>
    </tr>
    <tr>
      <td>Secret Word/td></td>
      <td>Input</td>
      <td>Secret word associated with API Key</td>
      <td>Website</td>
    </tr>
  </tbody>
</table>

Translation on Checkout page for title and description fields
In order to change the translation for title or description in different store view, navigate to System -> Configuration -> Sales -> Payment Methods. In the current configuration scope settings, change from default config to the store view you would like to conduct the translation in.

<h3>Order Statuses</h3>
<table>
  <tbody>
    <tr>
      <th>Lean Pay Status</th>
      <th>Magento Status</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>PENDING</td>
      <td>PENDING PAYMENT</td>
      <td>Pending orders are brand new orders, application for which have not been approved eitder declined yet.</td>
    </tr>
    <tr>
      <td>SUCCESS</td>
      <td>PROCESSING</td>
      <td>Processing means that Leanpay has approved a loan application and order is ready to be fulfilled</td>
    </tr>
    <tr>
      <td>CANCELED</td>
      <td>CANCELED</td>
      <td>Cancelled means tdat application eitder been rejected by Leanpay or customer has clicked on tde “x”</td>
    </tr>
    <tr>
      <td>EXPIRED</td>
      <td>CANCELED</td>
      <td>This status occurs when customer is not doing anything for way too long on the leanpay’s page</td>
    </tr>
  </tbody>
</table><br>
