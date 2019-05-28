* Wireless networking is a highly popular mean to connect to the Internet nowadays. 

* The most common type of wireless security methods are Wired Equivalent Privacy (WEP) and Wi-Fi Protected Access (WPA)

  * WEP is a weak security standard: the passwords user can be cracked in few minutes with a basic computer and available software tools. 

    WEP is an old IEEE 802.11 standard from 1997.

    WEP was superseded by the WPA in 2003

  * The current standard which improves security is WPA2.

     WPA2 uses an encryption device that encrypts the network with a 256-bit key

* Open network is such a network which does not require you to enter a WPA to WPA2 security code.

  * Any and all information sent over such an unsecured wireless network is information that is sent in plain sight for anyone to grab over the air. Just by connecting to an open network you are potentially opening your computer to someone else on that wireless network.
  * It's really not safe to connect to an unknown open wireless network, particularly if you're going to be transferring any kind of sensitive information, such as your online banking password.

* Recommendations to mitigare risks:

  * Wherever possible stick to well-known networks, like Starbucks. These Wi-Fi networks are likely less suspect because the people and companies operating them are already getting money out of you.

  * Stick with HTTPs: When you browse over HTTPS, people on the same Wi-Fi network as you can't snoop on the data that travels between you and the server of the website you're connecting to. Over HTTP? It's relatively easy for them to watch what you're doing.

  * Be very wary of signing up for public Wi-Fi access if you're getting asked for a bunch of personal details, like your email address or your phone number. If you absolutely have to connect to networks like this, stick to places you trust (see above) and consider using an alternative email address that isn't your primary one.

  * Cut off the features that enable frictionless file sharing on your devices. On a PC, that means going to **Network and Sharing Center**, then **Change advanced sharing settings**, then **Turn off file and printer sharing**. For Macs, go to **System Preferences**, then **Sharing**, and unselect everything. Then head to *Finder*, click on *AirDrop*, and select **Allow me to be discovered by: No One**. For iOS, just find AirDrop in the Control Center and turn it off.

  * Read up on the attached terms and conditions before you connect yourself to a public Wi-Fi connection.

  * Install a VPN or Virtual Private Network client on your devices. It encrypts data traveling to and from your laptop or phone, and hooks you up to a secure server—essentially making it harder for other people on the network, or whoever is operating the network, to see what you're doing or grab your details.

  * As an alternative option "Yandex.Protect: secure Wi-Fi connections" can be used. 

    The Protect system in Yandex Browser uses a proprietary method for securing Wi-Fi connections. This mechanism is implemented in Yandex Browser for desktop, as well as for smartphones and Android-based tablets.

    When secure Wi-Fi is enabled, data sent over the internet passes through a special encrypted channel. The data transfer rate may be slightly slower, because the page is sent to the Yandex encryption server before it is returned to the user.

* 802.1xEAP

  The Extensible Authentication Protocol (EAP) is a layer 2 process that allows a wireless client to authenticate to the network. 

  One of the concerns in wireless is allowing a WLAN client to communicate to devices behind an Access Point. Three standards define this process: EAP, 802.1x, and Remote Authentication Dial In User Service (RADIUS). EAP defines a standard way of encapsulating authentication information, such as a username and password or a digital certificate that the Access Point (a networking hardware device that allows other Wi-Fi devices to connect to a wired network) can use to authenticate the user. 802.1x and RADIUS define how to packetize the EAP information to move it across the network.

* Wireless network cards pre-installed in most of the modern laptops make is fairly easy for cyber-criminalists to access wireless networks or to hack into them. 

  * To prevent unauthorized access [Wireless intrusion prevention system](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwi86PrUqr7iAhUN_SoKHR71DUsQFjAAegQIAxAB&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FWireless_intrusion_prevention_system&usg=AOvVaw0XyWywIcv5CWn6rn1ycTFq) (WIPS) or [Wireless Intrusion Detection Systems](https://www.bastille.net/blogs/2018/7/24/wireless-intrusion-detection-systems-wids) (WIDS) are used. 
  * If router security is not activated or if the owner deactivates it for convenience, it creates a free hotspot. 
  * Built-in wireless networking might be enabled by default, without the owner realizing it, thus broadcasting the laptop's accessibility to any computer nearby.
  * Modern operating systems make it fairly easy to set up a PC as a wireless LAN "base station", thus allowing all the PCs in the home to access the Internet through the "base" PC.
    * Lack of knowledge among users about the security issues may allow others nearby access to the connection.
    * If an employee (trusted entity) brings in a wireless router and plugs it into an unsecured switchport, the entire network can be exposed to anyone nearby.

* Effective countermeasures are disabling open switchports during switch configuration, VLAN configuration to limit network access and port security.

  * It is simple to make configuration changes to multiple ports on a switch. If a range of ports must be configured, use the interface range command: 

    Switch(config)# **interface range** *type module*/*first-number* – *last-number*

    Switch(config-if)# shutdown

  * Another way to secure ports is by implementing a feature called port security. Port security limits the number of valid [MAC address](https://en.wikipedia.org/wiki/MAC_address) allowed on a port. The MAC addresses of legitimate devices are allowed access, while other MAC addresses are denied.

    Port security can be configured to allow one or more MAC addresses. If the number of MAC addresses allowed on the port is limited to one, then only the device with that specific MAC address can successfully connect to the port.

    If a port is configured as a secure port and the maximum number of MAC addresses is reached, any additional attempts to connect by unknown MAC addresses will generate a security violation. 

    Port security is enabled on the interface using the *switchport port-security* command.

    Ways to configure port security:

    * Static secure MAC addresses - MAC addresses that are manually configured on a port by using the *switchport port-security mac-address <u>targeted-mac-address</u>* interface configuration mode command. MAC addresses configured in this way are stored in the address table and are added to the running configuration on the switch.

    * Dynamic secure MAC addresses - MAC addresses that are dynamically learned and stored only in the address table. MAC addresses configured in this way are removed when the switch restarts or the port goes down.

    * Sticky secure MAC addresses - MAC addresses that can be dynamically learned or manually configured, then stored in the address table and added to the running configuration until the switch restarts.

      To configure an interface to convert dynamically learned MAC addresses to sticky secure MAC addresses and add them to the running configuration, you must enable sticky learning. Sticky learning is enabled on an interface by using the switchport port-security mac-address sticky interface configuration mode command.

      Sticky secure MAC addresses can also be manually defined. When sticky secure MAC addresses are configured by using the *switchport port-security mac-address sticky <u>targeted-mac-address</u>* interface configuration mode command, all specified addresses are added to the address table and the running configuration.

    An interface can be configured for one of three violation modes, specifying the action to be taken if a violation occurs:

    - Protect - When the number of secure MAC addresses reaches the limit allowed on the port, packets with unknown source addresses are dropped until a sufficient number of secure MAC addresses are removed, or the number of maximum allowable addresses is increased. There is no notification that a security violation has occurred.

    - Restrict - When the number of secure MAC addresses reaches the limit allowed on the port, packets with unknown source addresses are dropped until a sufficient number of secure MAC addresses are removed, or the number of maximum allowable addresses is increased. In this mode, there is a notification that a security violation has occurred.

    - Shutdown - In this (default) mode, a port security violation causes the interface to immediately become error-disabled and turns off the port LED. It increments the violation counter. When a secure port is in the error-disabled state, it can be brought out of this state by entering the shutdown interface configuration mode command followed by the no shutdown command.

      To change the violation mode on a switch port, use the *switchport port-security violation {protect | restrict | shutdown}* interface configuration mode command.

  * It is a security best practice to configure all unused ports to a **black hole VLAN** that is not used for anything on the network.

* In order to make connections between a router and wireless devices faster and easier WPS (Wi-Fi Protected Setup) can be used. 

  * **WPS works only for wireless networks that use a password** that is encrypted with the WPA Personal or WPA2 Personal security protocols. WPS doesn't work on wireless networks that are using the deprecated WEP security, which can be cracked easily by any hacker with a basic set of tools and skills.
  * In a standard setup, you can't connect a wireless device to a wireless network unless you know the network name (also named SSID) and its password (also called WPA-PSK key). Let's assume that you want to connect a device, like your smartphone, to your wireless network. On your device, you must first pick the network that you want to connect to and then enter its security password. Without performing both steps, you cannot connect to the WiFi network.

* Setting up a secure home network:

  * Change your SSID (Service Set Identifier). This makes it harder for hackers to identify what type of router you have, thereby, preventing them from exploiting known vulnerabilities. 
  * Change your default admin credentials. Routers usually come with weak usernames and passwords by default. If a hacker determines what router you have, they can look for its default credentials by going to sites like [RouterPasswords](http://www.routerpasswords.com/) and[ DefaultPassword](http://defaultpasswords.in/). Use strong passwords that are both long (16–20 characters) and complicated.
  * Make sure to turn on WPA2 encryption with AES (Advanced Encryption Standard), if possible. TKIP (Temporary Key Integrity Protocol) is better than nothing but AES is always be preferable.
  * Disable remote access to your router’s admin panel. The login credentials you send through the air may be intercepted by hackers. Disabling remote access prevents hackers from accessing your admin panel even if they were somehow able to break in wirelessly.
  * If your router supports built-in firewall - make sure it is enabled. 
  * Regularly update your software — especially your router firmware. Older firmware will have vulnerabilities which hackers can exploit. Also, you might miss important security features available only on the updated version. Firmware updates are usually rare so make sure to regularly check the manufacturer’s website for the latest version.

  