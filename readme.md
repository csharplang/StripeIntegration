
# Stripe Integration
Using Checkout in an ASP.NET Core MVC application


* Install-Package Stripe.net -Version 25.19.0


* More Deatils: https://stripe.com/docs/checkout/aspnet

### Code Example: 
```CSharp
public IActionResult Charge(string stripeEmail, string stripeToken)
{
    var customers = new CustomerService();
    var charges = new ChargeService();

    var customer = customers.Create(new CustomerCreateOptions
    {
        Email = stripeEmail,
        SourceToken = stripeToken
    });

    var charge = charges.Create(new ChargeCreateOptions
    {
        Amount = 500,
        Description = "Sample Charge",
        Currency = "usd",
        CustomerId = customer.Id
    });

    return View();
}
```

