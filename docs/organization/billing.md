(organization-billing)=
# Billing

CrateDB Cloud offers flexible billing options to accommodate various needs and
preferences. We only bill for actual usage of services, meaning there are no
flat fees or minimum payments.

## Billing Information 

In the Billing tab under the Organization overview, you can add and edit your
billing information, including your company address, country of residence, VAT
info, invoice email, phone contacts, and more. You need to fill out this
information whenever you use a paid offer on CrateDB Cloud, regardless of the
payment method.


## Subscriptions

After adding your billing information, you can add a subscription (payment
method). We currently support the following payment methods:

- **Cloud Marketplaces**: Available on [AWS](https://aws.amazon.com/marketplace/pp/prodview-l7rqf2xpeaubk),
  [Azure](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/crate.cratedbcloud), 
  and [GCP](https://console.cloud.google.com/marketplace/product/cratedb-public/cratedb-gcp) Marketplaces.
- **Credit Card**: Available worldwide. We use Stripe as our payment provider.
- **Bank Transfer**: Available in the EU. We use Stripe as our payment provider.
- **Custom Contract**: For large individual deployments, [contact](https://cratedb.com/contact) our sales team.

:::{tip}
**Marketplace Committed Spend:** All three marketplace offerings
(AWS, Azure, GCP) can be applied towards any committed spend agreement (e.g., MACC)
you have with the cloud provider. This effectively reduces your committed spend
balance and allows you to use CrateDB as if it were a native service provided by
the cloud provider.
:::

### Setup New Subscription

::::{tab} Cloud Marketplaces
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Navigate to the **"Billing"** tab on the right side.
3. Add your billing information.
4. Click on **"Add Payment Method"**.
5. Select your preferred cloud marketplace.
6. Follow the instructions to sign up for **CrateDB Cloud** through the selected marketplace.
7. After completing the subscription in the marketplace, you will be redirected to CrateDB Cloud.
8. Connect one of your organizations to the created marketplace SaaS subscription.

**You are now ready to deploy a cluster.**

When you deploy a cluster, the usage will be reported regularly to the
marketplace as usage amount in USD, and it will appear on your regular cloud
provider's invoice. Depending on your settlement currency, a conversion may be
applied.
::::

::::{tab} Credit Card
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Navigate to the **"Billing"** tab on the right side.
3. Add your billing information.
4. Click on **"Add susbscription"**.
5. Click on **"Pay with credit or debit card"**.
6. Fill out the required information and click **"Save"**.

**You are now ready to deploy a cluster.**

The payment cycle is monthly and aligns with the calendar month. You will be charged
for the previous period's usage and will receive an invoice at the email address
you provided. If needed, you can add a new credit card to replace the current one.
::::

::::{tab} Bank Transfer
<br>

1. Register for an account on the [CrateDB Cloud sign-in page](https://console.cratedb.cloud/).
2. Navigate to the **"Billing"** tab on the right side.
3. Add your billing information.
4. Click on **"Add Payment Method"**.
5. Click on **"Ask to enable"** next to **"Pay via Bank Transfer"**. Complete
  the form, and our team will contact you to process your request.

**After** your request has been approved:

1. Click on **"Add Payment Method"**.
2. Click on **"Pay via Bank Transfer"**.

**You are now ready to deploy a cluster.**

The payment cycle is monthly and aligns with the calendar month. You will be charged
for the previous period's usage, and an invoice will be sent to the email address
you provided. Payment is due within the specified terms.

:::{caution}
**Bank transfer payment is currently available only within the EU.**

These payments are processed by Stripe and invoiced in Euros at a fixed USD/EUR 
exchange rate. You can find the current exchange rate within the CrateDB Cloud
Console after setting up the bank transfer payment method.
:::

::::

::::{tab} Custom Contract
<br>

Custom contracts are individually tailored to your needs. Please 
[contact](https://cratedb.com/contact) our sales team to set up a custom contract
that fits your requirements.
::::


:::{note}
To remove a subscription, please contact support.
:::

## Usage Reporting

Whenever you use a paid offer in CrateDB Cloud, we collect your usage
information, including the cluster compute and storage size and the number of
nodes deployed. You can view this usage in the CrateDB Cloud Console, where
you'll find a usage snapshot for the current calendar month, the current cost
for the deployed service, and any available credits that might be applied to
the current usage period. Be aware that the billing period might deviate from
the shown calendar month usage.


## Credits

Credits are another way to pay for CrateDB Cloud services and can be used together
with other payment methods. Credits are applied to your account and are used up
first before any other payment method is charged. This means that if credits are
available, you will not be charged, nor will any usage be reported to your
payment provider. You can see the remaining credits and their validity date on
the Billing and Usage page.

There is also the option to purchase more credits at a discount by
[contacting](https://cratedb.com/contact) our sales team. 

:::{tip}
**Free Trial Credits**: If you just signed up, you have the option to enable
$200 of credits that can be used for any paid cluster. To enable these credits,
you need to provide a valid payment method, which will only be charged if you
have used up your credits.
:::
