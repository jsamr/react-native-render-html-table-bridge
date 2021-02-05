<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [@native-html/table-plugin](./table-plugin.md)

## table-plugin package

## Functions

|  Function | Description |
|  --- | --- |
|  [cssRulesFromSpecs(specs)](./table-plugin.cssrulesfromspecs.md) | Create css rules from a specification object. |
|  [useHtmlTableProps({ key, style, tnode }, tableConfig)](./table-plugin.usehtmltableprops.md) | Extract props for the HTMLTable component from renderer function arguments. This function is especially usefull for custom table renderers. |

## Interfaces

|  Interface | Description |
|  --- | --- |
|  [HTMLTableBaseProps](./table-plugin.htmltablebaseprops.md) | Base props for HTMLTable original and custom components. |
|  [HTMLTableProps](./table-plugin.htmltableprops.md) | Props for HTMLTable component. |
|  [HTMLTableStats](./table-plugin.htmltablestats.md) | An object holding information on the table shape. |
|  [TableAccurateContentHeightState](./table-plugin.tableaccuratecontentheightstate.md) | This content height state appears when the real table height is available, after the DOM has been mounted in the <code>WebView</code>. |
|  [TableConfig](./table-plugin.tableconfig.md) | This object defines how the table component can be customized. |
|  [TableHeuristicContentHeightState](./table-plugin.tableheuristiccontentheightstate.md) | This content height state is available on mount, before the real height is known from the DOM. |
|  [TableStyleSpecs](./table-plugin.tablestylespecs.md) | An object describing how to generate styles. See [cssRulesFromSpecs()](./table-plugin.cssrulesfromspecs.md)<!-- -->.<img src="https://raw.githubusercontent.com/native-html/table-plugin/master/images/TableStyleSpecs.png" /> |

## Variables

|  Variable | Description |
|  --- | --- |
|  [defaultTableStylesSpecs](./table-plugin.defaulttablestylesspecs.md) | Default styles attributes.<img src="https://raw.githubusercontent.com/native-html/table-plugin/master/images/TableStyleSpecs.png" /> |
|  [HTMLTable](./table-plugin.htmltable.md) | A component capable of rendering a html string which root tag is a table tag. This component should not be used directly, except with custom renderers. |
|  [TableRenderer](./table-plugin.tablerenderer.md) | The renderer component for the table element. This renderer is fully scalable, and will adjust to <code>contentWidth</code> and <code>computeEmbeddedMaxWidth</code>. It also features <code>onLinkPress</code>. |

## Type Aliases

|  Type Alias | Description |
|  --- | --- |
|  [TableContentHeightState](./table-plugin.tablecontentheightstate.md) | An object describing the present knowledge of content height. |
