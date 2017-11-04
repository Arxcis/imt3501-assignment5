# Report Assignment 5 - Threat Modeling and Abuse Cases

### Contributors

| Name              | Student no. | Track             |
| ----------------- | ----------- | ----------------- |
| Jonas J. Solsvik  | 473193      | 16HBPROGA         |
| Kent Wincent Holt | 473209      | 16HBPROGA         |
| Eldar             | 473180      | 16HBPROGA         |



### Task a) 

#### Size of code base / complexity

*Text: Study the application very well, and try to understand its architecture (components and relationships) and its behaviour. Use suitable diagrams to model the application (not Data Flow Diagram).*

I am studying the following github repository:

```http
https://github.com/NetEase/pomelo
```

Getting overview of the complexity of the codebase by using the tool CLOC to count lines of code:

```sh
PS C:\Users\Bruker\github\NetEase\pomelo> cloc .
     146 text files.
     142 unique files.
Complex regular subexpression recursion limit (32766) exceeded at script/cloc-1.72.pl line 9262.
      96 files ignored.

github.com/AlDanial/cloc v 1.72  T=2.00 s (63.5 files/s, 8153.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
JavaScript                     104           1998           2346          10786
Markdown                         2            140              0            539
JSON                            15              9              0            340
CSS                              1             11              0             65
HTML                             1              0              0             57
Bourne Shell                     2              0              0              6
YAML                             1              0              0              5
DOS Batch                        1              0              0              4
-------------------------------------------------------------------------------
SUM:                           127           2158           2346          11802
-------------------------------------------------------------------------------
```

```sh
PS C:\Users\Bruker\github\NetEase\pomelo> cloc lib/
      71 text files.
      71 unique files.
      22 files ignored.

github.com/AlDanial/cloc v 1.72  T=0.50 s (142.0 files/s, 19522.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
JavaScript                      71           1155           1975           6631
-------------------------------------------------------------------------------
SUM:                            71           1155           1975           6631
-------------------------------------------------------------------------------
```

```sh
PS C:\Users\Bruker\github\NetEase\pomelo> cloc test/
      26 text files.
      26 unique files.
      33 files ignored.

github.com/AlDanial/cloc v 1.72  T=0.50 s (52.0 files/s, 6228.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
JavaScript                      23            457             17           2541
JSON                             3              3              0             96
-------------------------------------------------------------------------------
SUM:                            26            460             17           2637
-------------------------------------------------------------------------------
```


#### Architecture overview diagram


#### Trust boundaries

**Client <---> Game-server**

**Admin-tool(cli/web) <---> Game server**

**Log/config <---> Game server**

**Persistent data storage <---> Game server**


### Task b)

*Text: Based on the understanding of the system, develop a use case and abuse diagram that has at least two actors and five use cases and four abuse cases.*
- You can use the tool SeaMonster for this task.

### Task c)

*Text: Follow the STRIDE methodology we discussed in the lecture to perform threat modeling:*
# Report Assignment 5 - Threat Modeling and Abuse Cases


## Contributors

| Name              | Student no. | Track             |
| ----------------- | ----------- | ----------------- |
| Jonas J. Solsvik  | 473193      | 16HBPROGA         |
| Kent Wincent Holt | 473209      | 16HBPROGA         |
| Eldar             | 473180      | 16HBPROGA         |


<br>

## Table of Contents

- [task a)](#task-a)
    + [Size of Code base](#size-of-codebase)
    + [Architecture Overview](#architecture-overview)
    + [Trust boundaries](#trust-boundaries)
    
- [task b)](#task-b)
    + [Abuse case diagram](#abuse-case-diagram)
    + [Use Actors](#use-actors)
    + [Use Cases](#use-cases)
    + [Abuse Actors](#abuse-actors)
    + [Abuse Cases](#abuse-cases)
    
- [task c)](#task-c)
    + [S T R I D E](#stride)

- [References](#references)

<br>


<a href="#task-a"></a>
## Task a) 

*Text: Study the application very well, and try to understand its architecture (components and relationships) and its behaviour. Use suitable diagrams to model the application (not Data Flow Diagram).*

We are studying the following github repository:

```http
https://github.com/NetEase/pomelo
```

<a href="#size-of-codebase"></a>
### Size of code base

Getting overview of the complexity of the codebase by using the tool CLOC to count lines of code:

```sh
PS C:\Users\Bruker\github\NetEase\pomelo> cloc .
     146 text files.
     142 unique files.
Complex regular subexpression recursion limit (32766) exceeded at script/cloc-1.72.pl line 9262.
      96 files ignored.

github.com/AlDanial/cloc v 1.72  T=2.00 s (63.5 files/s, 8153.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
JavaScript                     104           1998           2346          10786
Markdown                         2            140              0            539
JSON                            15              9              0            340
CSS                              1             11              0             65
HTML                             1              0              0             57
Bourne Shell                     2              0              0              6
YAML                             1              0              0              5
DOS Batch                        1              0              0              4
-------------------------------------------------------------------------------
SUM:                           127           2158           2346          11802
-------------------------------------------------------------------------------
```

```sh
PS C:\Users\Bruker\github\NetEase\pomelo> cloc lib/
      71 text files.
      71 unique files.
      22 files ignored.

github.com/AlDanial/cloc v 1.72  T=0.50 s (142.0 files/s, 19522.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
JavaScript                      71           1155           1975           6631
-------------------------------------------------------------------------------
SUM:                            71           1155           1975           6631
-------------------------------------------------------------------------------
```

```sh
PS C:\Users\Bruker\github\NetEase\pomelo> cloc test/
      26 text files.
      26 unique files.
      33 files ignored.

github.com/AlDanial/cloc v 1.72  T=0.50 s (52.0 files/s, 6228.0 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
JavaScript                      23            457             17           2541
JSON                             3              3              0             96
-------------------------------------------------------------------------------
SUM:                            26            460             17           2637
-------------------------------------------------------------------------------
```

<a href="#architecture-overview"></a>
### Architecture overview

The goals of Pomolo is to provide a fast, scalable, easy to use and powerfull framework for setting up serverclusters for games or similar applications.
The application is used to define servers, behaviour and communication. Servers must be part of frontend, backend or master. The frontend works as a router, for the client trafic, to the backend where the main logic is. Communication between the servers is done via **R**ermote **P**rocessing **C**alls.
Pomolo atempts to be as generall as possible, allowing it to be used for as much as possible. Pomolo is intended to be used with additional tools and plugins. 
<br>

<a href="#trust-boundaries"></a>
### Trust boundaries

**Client <---> Game-server**

The dataflow that crosses this boundary, can be any external entity trying to connect too the application. The incomming data should be checked for **S**poofing, **D**enial of service and **E**levation of privileges. The outgoing traffic should be checked for **S**poofing, **T**ampering, **R**epudiation, **I**nformation disclosure, **D**enial of service and **E**levation of privileges.

**Admin-tool (cli/web) <---> Game server**

The Admin-tool can be accessed by an external client and should be checked for the same threats as the Client <---> Game-server boundary. 

**Log/config storage <---> Game server**

The information of logs and config files can tell an attacker a lot about the behaviour of the system ontop of what the Pomolo sourcecode already does. Config files should not be changed by the server processes, only read. The Log files should only be changed by the server, not read or sendt by the server processes. The dataflow should be checked for **I**nformation disclosure and **S**poofing when writing logs. When using configuration files, **S**poofing, **T**ampering, **R**epudiation, **I**nformation disclosure, **D**enial of service and **E**levation of privileges.

**Front-end <---> Back-end**

The information that flows here might just be briefly checked (e.g. Header info) but nothing inside the body


<br>

<a href="#task-b"></a>
## Task b)

*Text: Based on the understanding of the system, develop a use case and abuse diagram that has at least two actors and five use cases and four abuse cases.*

<a href="#use-case-diagram"></a>
### Use case diagram
<br>

<a href="#use-actors"></a>
### Use Actors

__Client developer__
Will develop client side code using the various SDK's provided by the Pomelo framework. Experienced client developer's may also develop their own SDK's.

__Server developer__
Will develop the services on server side, and set up connections between different services.

__System administrator__
Monitors servers. Manage scaling, maintainance of servers.
<br>

<a href="#use-cases"></a>
### Use cases

__1. Subscribe to events defined by the game server application__
*Actor:Client developer*

__2. Notify server about client state__
*Actor:Client developer*

__3. Manage the server cluster from a master server__
*Actor: Sysadmin*

- Spawn/shut down servers.
- Monitor resource usage and status. 

*References:* 
[wiki/Builtin-Components#master](https://github.com/NetEase/pomelo/wiki/Builtin-Components#master)

__4. Read/Configure logs of server events__
*Actor: Sysdmin*
- Log events from servers.
[wiki/Log-Managment](https://github.com/NetEase/pomelo/wiki/Log-Management)

__5. Configure Remote Process Calls(RPC's) between servers__
*Actor: Server developer*
<br>

<a href="#abuse-actors"></a>
### Abuse Actors

__Dishonest player__

*Motivation:* Most online games have some element of competition. A considereable amount of players are willing to do "whatever it takes" to gain an competitive advantage over others. 
*Expected skill level - Low/moderate:* why?? 

__Sensitive information thief__

*Motivation:* Sensitive information has monetary value in the right hands. A thief would be interested to exploit weak systems, to uncover secrets about it's users. For instance passwords, play time, and more. As the service scales, more potential value could be extracted from it's users.
*Expected skill level - Moderate/high:* why?? 

__Dishonest business competitior__

*Motivation:* Would benefit from destabilizing your system, hurting the reputation of your service. This would make it easier to convince players to change to other services.
*Expected skill level - High:* This actor will probably hire professional hackers, because they have economic insentive to do so.


__Disgruntled insider__
*Motivation:* If an employee feels badly treated, in extreme cases he or she might think it is a good idea to cause the company harm.
*Expected skill level - Expert:* No one knows the system better than the insiders.
<br>

<a href="#abuse-cases"></a>
### Abuse cases
__1. Launch overwhelming traffic from client(s)__
*Actor: dishonest business competitor*
- Creation of fake game clients to overload the servers. The clients can be created anywhere, on any platform, since the server uses open internet protocols to connect. 
- A single client could also cause problems if it were to find vurnerabilities which would enable exessive traffic.

__2. Client spoofing__

- A client may spoof the identity of other clients, to gain access to sensitive information. It could also be used to gain in-game advantages, if the game server is hosting a competitive game.

__3. Unauthorized access to logs__

- How are the logs accessed?
- Are they stored in plain text?
- Where are the logs stored?
- Are there backups?
- Do they transfer over the network?

__4. Server broadcast Area of Interest manipulation__

- In many cases the server will broadcast information to clients using an Area of Interest policy. A client will only recieve information within a defined area of interest. If this area of interest system can be tampered with, an attacking client may gain a competetive advantege by increasing it's Area of Interest, and decreasing other players Area of Interest.


<br>

Here is a more indept view of the Area of Interest manipulation in form of an attack tree.

<object data="./image/attackTree.pdf" type="application/pdf" width="700px" height="700px">
    <embed src="./image/attackTree.pdf">
    </embed>
</object>

<a href="#task-c"></a>
## Task c)

*Text: Follow the STRIDE methodology we discussed in the lecture to perform threat modeling:*

<a href="#strid"></a>
### S T R I D E
- Identify trust domains, the trust boundaries and the attack surface.
- Create a DFD diagram that represent of the application.
- Identify the threat types to each element.
- Identify at least ten possible threats: at least two for a data flow, two for a adata store, and four for processes, two for external entities. Discuss each threat and how it can be realized and what it can affect.
- Identify one possible mitigation for each threat. 

<a href="#references"></a>
### References to help you: 
1. [OWASP threat modeling guide](https://www.owasp.org/index.php/Application_Threat_Modeling) 
2. [OWASP threat modeling cheat sheet](https://www.owasp.org/index.php/Threat_Modeling_Cheat_Sheet)
3. [Microsoft threat modeling guide](https://msdn.microsoft.com/enus/library/ff648644.aspx)
4. [How to describe a Misuse/Abuse case](http://www.nik.no/2001)
5. The threat modeling book - Adam Shostack. Threat modeling: Designing for security. 