# Off For Shabbos .NET

_Current Version: 0.0.1_

Jewish Law<sup>1</sup> prohibits earning money during the Jewish Sabbath.  Traditionally, this meant observant Jewish bussinessmen would close their store or business for the day... but how do we "close the store" in a modern "always available" online marketplace?

The "Off For Shabbos" project makes addresses the problem by dividing your online store in half.  The majority of your website - product listings, shopping cart, FAQ, shipping policies, etc - don't charge the customer any money.  There's no reason for OffForShabbos to disable those pieces!  Instead, we disable only the checkout page.  Your customers orders will be cached and processed after Shabbos ends.

## Quickstart

Install the package using Nuget.

> Install-Package OffForShabbos.Net

Setup a scheduled job (cron, Scheduled Task, etc) to run `OffForShabbos.Process.exe` once a day.  The process app will check for settings in a `Web.config` or `App.config` file.

### For MVC projects

Add the `OffForShabbosFilterAttribute` to your global filter collection in `Global.asax`.

    filters.Add(new OffForShabbosFilterAttribute(new OffForShabbosOptions {
        LocationCode = "JLM"
    });

### For OWIN projects

Add the `OffForShabbosMiddleware` to your app configuration in `Startup.cs`.

    app.UseOffForShabbos(new OffForShabbosOptions {
        LocationCode = "JLM"
    });

You can also specify configuration options in your `Web.config` file using the `<off-for-shabbos>` configuration section.

## Built With

* [MyZmanim.com]

## Contributing

Please read [CONTRIBUTING.md] for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Yaakov Yisroel Kosbie** - *Initial work* - [Soris Software](http://www.sorissoftware.com)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* B&H Photo in New York who have continued to observe the rules of Shabbos even in an era of immense pressure to give in.  Their vigilance is a large part of the motivation for this project.