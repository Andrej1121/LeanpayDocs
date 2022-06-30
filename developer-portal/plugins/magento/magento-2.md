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
		<a href="https://storage.googleapis.com/stoplight-resources/Download/leanpay-magento2-v3.zip" download>
		<button class="btn" style="width:30%"><i class="fa fa-download"></i> Prenos vtičnika</button>
  </div>
</body>
</html>




## Plugin Installation Guide via files

- Download Files
- Upload the files into Magento Root
- In terminal - bin/magento module:enable Leanpay_Payment
- In terminal bin/magento setup:upgrade
- In terminal - bin/magento cache:flush
- Navigate to Stores -> Configuration -> Sales -> Payment Methods, Leanpay tab
- Enable extension

## Plugin Installation Guide via Composer (V POSODABLJANJU)

- In terminal - composer require leanpay/payment
- In terminal - bin/magento module:enable Leanpay_Payment
- In terminal - bin/magento setup:upgrade
- In terminal - bin/magento cache:flush
- Navigate to Stores -> Configuration -> Sales -> Payment Methods, Leanpay tab
- Enable extension

## Configurations - Admin

After successful extension installation, you can see its configurations in Stores -> Configuration -> Sales -> Payment Methods, Leanpay.com tab

<h2>Configuration Table</h2>
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
	<tr>
      <td>Payment from Applicable Countries</td>
			<td>Select
				<ul>
				<li>All AllowedCountries</li>
				<li>*SpecificCountries</li>
				</ul>
			</td>
      <td>When enable leanpay</td>
      <td>Website</td>
    </tr>
	<tr>
		<td>Payment from Specific Billing Countries</td>
		<td>Select
				<ul>
				<li>All AllowedCountries</li>
				<li>*SpecificCountries</li>
				</ul>
		</td>
      <td>When enable leanpay</td>
      <td>Website</td>
    </tr>
  </tbody>
</table>
