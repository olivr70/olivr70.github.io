=# Tout sur le pilotage de OpenOffice


## en C#

Les Assembly qui définissent les types sont installés dans le GAC. Pour les lister en Powershell `[appdomain]::currentdomain.GetAssemblies()`.
Pour plus de détail voir [The Language Binding DLLs](https://wiki.openoffice.org/wiki/Documentation/DevGuide/ProUNO/CLI/Language_Binding_DLLs)
les [versions actuelles des DLL](https://www.openoffice.org/udk/common/man/spec/assemblyversioninghistory.html) pour Open Office 4.0.1 (release mai 2021)

Sont listés dans C:\Windows\Microsoft.Net\assembly\GAC_MSIL:
- cli_oootypes.dll                                    
- cli_uretypes.dll                                          
- cli_basetypes.dll      
Il y a aussi cli_ure.dll (qui définit les types WeakBase, WeakComponentBase, WeakAdapter dans *uno.util*) mais qui n'est pas listé.


### Difficultés
les librairies sont dans GAC_MSIL, sauf lib_cppuhelper qui se trouve dans GAC_32. Pour l'utiliser il faut donc que le projet
ait une plateforme 32 bits (Build / x86)



## Articles

### Sur l'utilisation en C#

Très peu de docs, on trouve des [exemples](https://api.libreoffice.org/examples/examples.html#CLI_examples)

### Sur l'utilisation en Java

- [Transparent Use of Office UNO Components](https://wiki.openoffice.org/wiki/Documentation/DevGuide/ProUNO/Java/Transparent_Use_of_Office_UNO_Components)
Présente l'utilisation de la classe  com.sun.star.comp.helper.Bootstrap.bootstrap() pour se connecter à LibreOffice


### Se connecter

Deux options : 
- haut niveau : [avec UnoUrlResolver](https://wiki.openoffice.org/wiki/Documentation/DevGuide/ProUNO/Importing_a_UNO_Object)
- bas niveau : voir [Opening a connection](https://wiki.openoffice.org/wiki/Documentation/DevGuide/ProUNO/Opening_a_Connection), puis [creating the bridge](https://wiki.openoffice.org/wiki/Documentation/DevGuide/ProUNO/Creating_the_Bridge)
  - on crée à la main une [XConnection](https://www.openoffice.org/api/docs/common/ref/com/sun/star/connection/XConnection.html)
  - puis une [BridgeFactory](https://www.openoffice.org/api/docs/common/ref/com/sun/star/bridge/BridgeFactory.html)
  - pour un exemple voir le projet JODConverter, et plus précisément [OfficeConnection](https://github.com/sbraconnier/jodconverter/blob/f2aee5ea9333a6025bf25ce9b24336c173e5b522/jodconverter-local/src/main/java/org/jodconverter/local/office/OfficeConnection.java)