# Teladoc Email Test

This project is a fully responsive and fluid email for mobile and desktop, based on a provided e-commerce template. It consists of five main sections: Header, Ribbon, Title, Content (tiles), and footer. The project was developed using HTML and CSS, and it is fully responsive and fluid, adapting to different screen sizes.

## Getting Started

To preview the email, open the `index.html` file in your browser.

The email was tested on physical devices, emulators and email testing tools such as Litmus and Email on Acid.

You can see screenshots of the email in different screen sizes, devices and email clients in the `Email_on_Acid_Screenshots` folder.

## Process

The email was developed using HTML and CSS.

The first step I took was to decide how to structure the email.

Typically, I would use a table structure, inline styles, and add media queries to handle responsiveness across different formats and viewports. However, upon examining the email's structure, with various product tiles organized differently, I opted for an approach we've been using in my recent role as an email developer. This approach involves employing two different structures for mobile and desktop versions, using a `table` structure for the desktop version and a `div` structure for the mobile version. This provides greater control over design, ease in bug correction, faster product development, and increased flexibility.

Resources were extracted with the assistance of Adobe Photoshop and then adapted in size with retina screens in mind, before being compressed to ensure resource optimization.

After developing the email, I proceeded to test functionality and adaptability across various devices, reviewing links, tokens, color contrast, compatibility, alternative text for images, among other elements. Finally, I conducted testing on real devices, emulators, and Email on Acid to ensure comprehensive quality assurance.

## Test questions and answers

### Question 2

In Salesforce Marketing Cloud, I would utilize AMPscript to incorporate dynamic content into the email. Here's the process:

Data Extension: Initially, we would set the dynamic content in the email based on data in the data extension, such as user information or product details.

AMPscript Variables: Within our HTML code, we'll substitute static content with AMPscript variables. For instance, replacing "Customer" with an AMPscript variable like "%%FirstName%%" for a personalized greeting: "Hello, %%FirstName%%".

Conditional Statements: AMPscript enables us to display varied content based on specific conditions. For example, we can tailor images or text according to a subscriber's preferences or past interactions.

Testing: Salesforce Marketing Cloud offers features allowing us to preview how our email will appear with dynamic content. Utilizing this, we can thoroughly test our email to ensure seamless functionality.

### Question 3

We can use the `Lookup` function to retrieve data from the `Customer_preference` data extension based on the `Customer ID`.

Assumptions:

The `Customer ID` is available in the send context.
The `Customer_preference` data extension has columns named `Title`, `Images`, `Copy Text`, and `CTA Copy` corresponding to the `Title/Product Name`, `Images/Product`, `Copy Text`, and `CTA Copy` respectively.
Here's an example with the first tile:

```html
%%[
    SET @customerID = AttributeValue("Customer ID")
    SET @title = Lookup("Customer_preference", "Title", "Customer ID", @customerID)
    SET @image = Lookup("Customer_preference", "Images", "Customer ID", @customerID)
    SET @copyText = Lookup("Customer_preference", "Copy Text", "Customer ID", @customerID)
    SET @ctaCopy = Lookup("Customer_preference", "CTA Copy", "Customer ID", @customerID)
]%%
<!-- Tile 3 -->
<tr class="row">
    <td>
        <table width="660" cellspacing="0" cellpadding="0" border="0" align="center" style="background-color: #ffffff; border-radius: 16px;" role="presentation">
            <tr>
                <td valign="middle" width="420"  style="vertical-align: middle;">
                    <table border="0" cellspacing="0" cellpadding="0" role="presentation" width="420" >
                        <tr>
                            <td style="padding-bottom: 11px; padding-left: 40px; text-align: left; line-height: normal;">
                                <h3 style="font-size: 32px; letter-spacing: 0px; line-height: 36px; color: #351f65; font-weight: 600;font-family: 'Times New Roman', Times, serif;">%%=v(@title)=%%</h3>
                            </td>
                        </tr>
                        <tr>
                            <td class="copy" style="text-align: left; padding: 0px 87px 20px 40px;">
                                <p style="color: #351f65; font-size: 14px; font-weight: 400; line-height: 20px;">%%=v(@copyText)=%%</p>
                            </td>
                        </tr>
                        <tr>
                            <td valign="middle" style="padding:10px 0"> 
                                <table align="left" cellpadding="0" cellspacing="0" border="0" role="presentation" style="font-family:Arial, Helvetica, sans-serif; font-size: 18px; line-height: 22px; margin: 0 auto; padding-left: 42px; width: 56%;">
                                    <tr>
                                        <td class="active" align="center" valign="middle" style="border-radius: 180px; background-color:#6240E8; mso-padding-alt: 10px 25px;">
                                            <a href="https://www.hello.com/" style="display:block; padding: 5px 25px; text-decoration: none; font-weight: 700; background-color:#6240E8; color: #FFFFFF;border-radius: 180px; width:100%; box-sizing: border-box;">
                                                %%=v(@ctaCopy)=%%
                                            </a>
                                        </td>
                                    </tr>
                                </table>
                            </td>
                        </tr>
                    </table>
                </td>
                <td align="right" valign="top" width="240"  style="vertical-align: top;">
                    <table align="right" border="0" cellspacing="0" cellpadding="0" role="presentation" width="240"  style="text-align: right;">
                        <tr>
                            <td align="center" class="align-center" style="text-align: center; vertical-align: middle; font-size: 0px; margin: 0px; line-height: 0;">
                                <picture>
                                    <source media="(max-device-width: 568px)" ><img height="250" src="%%=v(@image)=%%" width="170" border="0" class="align-center" style="display: block;padding-right: 20px;" alt=" ">
                                </picture>
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

We could repeat this process for each tile, ensuring that the `Customer ID` is available in the send context and that the `Customer_preference` data extension contains the necessary columns.

We could've also used a dynamic URL with UTM parameters for he CTA button like href="%%=RedirectTo(@UTMURLcta)=%%" to track the performance of the email.

## Credits

- All images were provided by Teladoc Health and stored in AWS S3: [aws.amazon.com/s3](https://aws.amazon.com/s3/)
- Testing was conducted using Email on Acid: [www.emailonacid.com](https://www.emailonacid.com/)
- Images were compressed using TinyPNG: [tinypng.com](https://tinypng.com/)

## Contributing

Contributions are welcome! If you find any bugs or have any suggestions, please create an issue or a pull request.

## Contact

For any questions or comments, please contact me at my email: simonjesusalvarado@gmail.com