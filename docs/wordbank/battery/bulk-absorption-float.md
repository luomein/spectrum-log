# Bulk, Absorption and Float

[reference](https://www.victronenergy.com/media/pg/Skylla-IP65/en/operation.html)

Voltage and current during different states in battery charging

![Seven stage charge curve for lead-acid batteries](https://www.victronenergy.com/media/pg/Skylla-IP65/en/image/1652514b3ef574.png)

> 4.2.1. Bulk

> Entered when the charger is started or when the battery voltage falls below 13.2 V / 26.4 V (due to a heavy load) during at least 1 minute. Constant current is applied until gassing voltage is reached (14.4 V / 28.8 V).

> 4.2.2. Battery Safe

> If absorption voltage is set higher than 14.4 V / 28.8 V, the rate of voltage increase beyond 14.4 V / 28.8 V is limited to 7mV/14mV per minute, in order to prevent excessive gassing.

> 4.2.3. Absorption

> After the absorption voltage has been reached, the charger operates in constant voltage mode.

> In case of adaptive charging, the absorption time is dependent on the bulk time, see section 3.2.

> 4.2.4. Automatic equalization

> If automatic equalization has been set to ‘on’, the absorption period is followed by a second voltage limited constant current period: see section 3.3. This feature will charge VRLA batteries to the full 100 %, and prevent stratification of the electrolyte in flooded batteries.

> Alternatively, manual equalization can be applied.

> 4.2.5. Float

> After float charge the output voltage is reduced to storage level. This level is not sufficient to compensate for slow self-discharge of the battery, but will limit water loss and corrosion of the positive plates to a minimum when the battery is not used.

> 4.2.6. Storage

> After float charge the output voltage is reduced to storage level. This level is not sufficient to compensate for slow self-discharge of the battery, but will limit water loss and corrosion of the positive plates to a minimum when the battery is not used.

> 4.2.7. Weekly battery ‘refresh’

> Once a week the charger will enter Repeated Absorption-mode during one hour to ’refresh’ (i. e. to fully charge) the battery


