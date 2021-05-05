# BML: Banzai Markup Language
---
This is a markup language used to configure [Banzai](https://github.com/egehurturk/Banzai.git) server. 


```
Currently under development 🤭 🎃
```
---

## Examples:

```banz
regulation ip_config {
	allow ip from 192.*.*.*
	deny  ip from 34.*.*.*
}

record HouseRecord {
	name
	addr
	price
}

action print_house_record_info() {
	HouseRecord r -> ("Seamus", "SF USA", "$45.6")
	printf "{$r.name} lives in {$r.addr} and it costs {$r.price}"
}


regulation hooks {
	do print_house_record_info()


	when ip localIp  from 192.168.8.* connects  	do  greet_local_user($localIp)
	when ip starWars from 23.*.*.*    connects      do  greet_star_wars($starWars)
	when ip lotr     from 98.*.*.*    requests      do  salute($lotr)
}

action greet_local_user(ipAddr) {
	printsf to {$ipAddr.host} "Welcome, {$ipAddr.host}:{$ipAddr.port}"
}

action greet_star_wars(ipAddr) {
	prints to {$ipAddr.host} "Hello, there! G'nral Kenobi!"
}

action salute(ipAddr) {
	prints to {$ipAddr.host} "Hello, yo, salute!"
}
```
