# CO2

<img src="https://travis-ci.org/thegreenwebfoundation/co2.js.svg?branch=master" />

We know computers use electricity, and because most of the electricity we use comes from burning fossil fuels to generate, there is an environmental cost to every upload and download we make over the internet.

We cando something about this though. The same way we use performance budgets make apps and website faster and cheaper to run, we can use carbon budgets to make them faster, cheaper and _greener_.

The CO2 package from [The Green Web Foundation][tgwf] lets you quickly estimate these emissions, to make measurable improvements as part of your workflow.

It does this by implementing the 1byte model as used by the Shift Project, as introduced in their report on CO2 emissions from digital infrastructure, [Lean ICT: for a sober digital][soberDigital], to return a number for the estimated CO2 emissions for the corresponding number of bytes sent over the wire.

It is currently used in the web performance tool [sitespeed.io][], to help developers build greener, more planet friendly digital services.

If you want to build this kind of environmental information into your own software, and want some advice, we'd be happy to hear from you - please open an issue, remembering to link to your project.

This is open source software, with all the guarantees associated, so if you want professional advice, to a deadline, and you have a budget please see the services offered by the [Green Web Foundation][tgwf-services].

[soberDigital]: https://theshiftproject.org/en/lean-ict-2/
[sitespeed.io]: https://sitespeed.io/
[tgwf]: https://www.thegreenwebfoundation.org/
[tgwf-services]: https://www.thegreenwebfoundation.org/services/


## Usage

```js

const CO2 = require('@tgwf/co2')
const bytesSent = 1_000_000
const co2Emission = new CO2();
estimatedCO2 = co2Emission.perByte(bytesSent)

console.log(`Sending a million bytes, had a carbon footprint of ${estimatedCO2.toFixed(3)} grams of CO2`)

```

Because different digital services and websites use different forms of power, there is also a module for checking if a domain uses green power or not, and whether the domains linked to on a page use green power as well.

```js

const greencheck = require('@tgwf/hosting')

// returns true if green, otherwise false
greencheck.check("google.com")

// returns an array of the green domains, in this case ["google.
greencheck.check(["google.com", "kochindustries.com"]) com"]

// returns an array of green domains, again in this case, ["google.com"]
greencheck.checkPage(["google.com"])

```

Please note, we currently look at just the carbon cost of _generating_ the electricity, similar to how the IEA does, not the full life cycle cost of the energy, which would include things like:

- the carbon associated with digging up the fuel
- the carbon associated with mining the materials to build the power stations, datacentres
- the end of life costs
- the maintenance costs over the life of the datacentres, power generation and end user devices, and the rest of the internet

We'd like to do this, and we know how complicated this is likely to be.


# Licenses

Apache 2.0

