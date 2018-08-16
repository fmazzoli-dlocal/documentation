---
description: >-
  Build your own pixel-perfect checkout flows across desktop and mobile, without
  worrying about PCI.
---

# Smart Fields

In order to be eligible for the easiest level of PCI compliance – [SAQ A](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment) – certain payment fields on the checkout page must be hosted securely. This requires you to host the information on an external payment gateway's domain and present the fields to your users in an iframe or with a redirect.

dLocal's Smart Fields solution accomplishes this by rendering an iframe to handle input of the following payment fields on your checkout page: Card Number, CVV and Expiration date.

This provides you with the ability to customize the look and feel of your web page while ensuring that you are compliant with PCI requirements.

### Fully Customizable Checkouts

![](../../.gitbook/assets/image.png)

Smart Fields defer as much of the styling of field components to you as possible. The layout, width, height, and outer styling \(`border`, `box-shadow`, `background`, etc.\) are left **completely in your control**.

{% hint style="info" %}
Currently only the all-in-one `card` Field is available \(you can try it below\). This design is aligned with the latest trends in checkout design.

Separate Smart Fields for CC Number, Expiration Data and CVV will be coming in the next few weeks.
{% endhint %}

Below is a live demo of our all-in-one `card`Field. Open on CodePen to make changes to the code in real time:

{% embed data="{\"url\":\"https://codepen.io/martindlocal/pen/MBeJdN\",\"type\":\"rich\",\"title\":\"Fields-simple-example\",\"description\":\"...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://codepen.io/favicons/favicon-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://s3-us-west-2.amazonaws.com/i.cdpn.io/2175964.MBeJdN.small.40f2b5d8-e211-40cd-8561-db7b53d92b68.png\",\"width\":384,\"height\":225,\"aspectRatio\":0.5859375},\"embed\":{\"type\":\"app\",\"url\":\"https://codepen.io/martindlocal/embed/preview/MBeJdN?height=300&slug-hash=MBeJdN&default-tabs=css,result&host=https://codepen.io&embed-version=2\",\"html\":\"<iframe src=\\\"https://codepen.io/martindlocal/embed/preview/MBeJdN?height=300&amp;slug-hash=MBeJdN&amp;default-tabs=css,result&amp;host=https://codepen.io&amp;embed-version=2\\\" style=\\\"border: 0; width: 100%; height: 300px;\\\" allowfullscreen></iframe>\",\"height\":300,\"aspectRatio\":null}}" %}



#### Ready to start accepting credit card payments right from your website? Setup Smart Fields today in 4 easy steps:

{% page-ref page="fields-setup-guide.md" %}

