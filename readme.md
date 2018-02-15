## Powerswitch API

Powerswitch has developed a new feature for retailers to access information about customers that are potentially switching. This is provided in the form of URL query params passed along when the user clicks the switch link on Powerswitch.

Here's a real example: 

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
