## Powerswitch API

Powerswitch has developed a new feature for retailers to access information about customers that are potentially switching. This is provided in the form of URL query params passed along when the user clicks the switch link on Powerswitch. We may add proper API endpoints for profiles/switches if there is demand.

Here's an example:

`?a=52+XXX+St%2C+XXX%2C+XXXX+XXXX%2C+New+Zealand&address_id=ChXXXXXVk2ohQW0RsKgzxaxeR88&electricity_icp=00XXXX3000WR9F6&electricity_plan=Super+Saver+Uncontrolled&estimated_usage=17501&profile_id=QRdAlAVjwj&x=175.6657305&y=-40.9368174`

```
{
  profile_id: "n21h1AAH",
  first_name: "example",
  last_name: "example",
  email: "example@example.com",
  a: "1 Example Street",
  x: "",
  y: "",
  address_id: "",
  electricity_icp: "",
  electricity_plan: "General Plan",
  gas_plan: "",
  gas_icp: "",
  estimated_usage: 12000,
}
```

### Keys:

- `switch_id` : The id of this switch.

- `profile_id` : The id of the users associated profile on Powerswitch. Always provided.

- `first_name` : The users first name.

- `last_name` : The users last name.

- `email` : The users email.

- `a` : The display string of the users address.

- `address_id` : The Google address API id.

- `x` : The address latitude.

- `y` : The address longitude.

- `<energy_type>_icp` : The ICP number. Always provided (one or both of gas or electricity).

- `<energy_type>_plan` : The users selected plan name. Always present (one or both of gas or electricity).

- `estimated_usage` : Estimate of usage in kWh/year.

### Tutorial

When a users on Powerswitch clicks the switch link it creates a `Switch` object in our database.

The repsonse is sent to the client which then redirects to the retailers join URL with the aforementioned query params in the URL.

The data could be stored, for reconciling confirmed switches, or as a way to fill in client side forms or however you see fit.

As a quick example in Ruby:

```
switch = Rack::Utils.parse_nested_query(query).deep_symbolize_keys
```

Implementation for accessing and using the provided data is up to retailers but if you need help or suggetions feel free to contact us.
