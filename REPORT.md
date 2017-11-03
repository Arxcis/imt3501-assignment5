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
- Identify trust domains, the trust boundaries and the attack surface.
- Create a DFD diagram that represent of the application.
- Identify the threat types to each element.
- Identify at least ten possible threats: at least two for a data flow, two for a adata store, and four for processes, two for external entities. Discuss each threat and how it can be realized and what it can affect.
- Identify one possible mitigation for each threat. 

### References to help you: 
1. [OWASP threat modeling guide](https://www.owasp.org/index.php/Application_Threat_Modeling) 
2. [OWASP threat modeling cheat sheet](https://www.owasp.org/index.php/Threat_Modeling_Cheat_Sheet)
3. [Microsoft threat modeling guide](https://msdn.microsoft.com/enus/library/ff648644.aspx)
4. [How to describe a Misuse/Abuse case](http://www.nik.no/2001)
5. The threat modeling book - Adam Shostack. Threat modeling: Designing for security. 
