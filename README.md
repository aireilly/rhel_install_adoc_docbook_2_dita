# AsciiDoc > Docbook > DITA transform

Testing out what an end-to-end AsciiDoc > DITA transform might look like.

## Set up

Install asciidoctor-reducer, DITA-OT, Java, and then:

```cmd
$ wget https://github.com/Saxonica/Saxon-HE/releases/download/SaxonHE12-4/SaxonHE12-4J.zip
```

## TODO

- Get the GH to publish a clean HTML5 output to GH pages
- AsciiDoc > Docbook:
  - `</preface>` > `</acknowledgements>`
  - `{_context}` > `_installing-RHEL`
  - `</informalexample>` ???
- DITA transform:
  - Get dbdita transform to run in GitHub action. Maybe: https://github.com/ipdxco/junit-xml-to-html/blob/main/action.yml
  - transform entrypoint is: `./dbdita/db2dita/docbook2dita.xsl`

## Roughwork

```cmd
$ asciidoctor -b docbook5 performing-a-standard-rhel-installation.adoc -o performing-a-standard-rhel-installation.xml

$ java -jar /home/aireilly/rhel_install_adoc_docbook_2_dita/SaxonHE12-4J/saxon-he-12.4.jar -xsl:./dbdita/db2dita/docbook2dita.xsl -s:./performing-a-standard-rhel-installation.xml -o:performing-a-standard-rhel-installation.dita

# Do some cleanup on performing-a-standard-rhel-installation.dita

$ dita -i performing-a-standard-rhel-installation.dita -f html5 -o ./out
```
