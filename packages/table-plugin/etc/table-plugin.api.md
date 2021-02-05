## API Report File for "@native-html/table-plugin"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { ComponentType } from 'react';
import { CustomBlockRenderer } from 'react-native-render-html';
import { CustomTagRendererProps } from 'react-native-render-html';
import { HtmlAttributesDictionary } from 'react-native-render-html';
import { RenderHTMLPassedProps } from 'react-native-render-html';
import { StyleProp } from 'react-native';
import type { TBlock } from '@native-html/transient-render-engine';
import { ViewStyle } from 'react-native';

// @public
export function cssRulesFromSpecs(specs?: TableStyleSpecs): string;

// @public
export const defaultTableStylesSpecs: TableStyleSpecs;

// @public
export const HTMLTable: ({ WebView, tableStyleSpecs, cssRules, html, sourceBaseUrl, animationType, computeHeuristicContentHeight, computeContainerHeight, webViewProps: userWebViewProps, style, onLinkPress, animationDuration, htmlAttribs, maxScale, ...stats }: HTMLTableProps) => JSX.Element;

// @public
export interface HTMLTableBaseProps extends HTMLTableStats {
    html: string;
    htmlAttribs?: HtmlAttributesDictionary;
    onLinkPress?: RenderHTMLPassedProps['onLinkPress'];
    WebView: ComponentType<any>;
}

// @public
export interface HTMLTableProps extends TableConfig, HTMLTableBaseProps {
}

// @public
export interface HTMLTableStats {
    numOfChars: number;
    numOfColumns: number;
    numOfRows: number;
}

// @public
export interface TableAccurateContentHeightState {
    // (undocumented)
    contentHeight: number;
    // (undocumented)
    type: 'accurate';
}

// @public
export interface TableConfig {
    animationDuration?: number;
    animationType?: 'none' | 'layout' | 'animated';
    computeContainerHeight?: (state: TableContentHeightState) => number | null;
    computeHeuristicContentHeight?: (state: HTMLTableStats) => number;
    cssRules?: string;
    displayMode?: 'normal' | 'embedded' | 'expand';
    maxScale?: boolean;
    sourceBaseUrl?: string;
    style?: StyleProp<ViewStyle>;
    tableStyleSpecs?: TableStyleSpecs;
    webViewProps?: any;
}

// @public
export type TableContentHeightState = TableHeuristicContentHeightState | TableAccurateContentHeightState;

// @public
export interface TableHeuristicContentHeightState {
    // (undocumented)
    contentHeight: number;
    // (undocumented)
    type: 'heuristic';
}

// @public
const TableRenderer: CustomBlockRenderer;

export default TableRenderer;

// @public
export interface TableStyleSpecs {
    cellPaddingEm: number;
    columnsBorderWidthPx: number;
    fitContainerHeight: boolean;
    fitContainerWidth: boolean;
    fontFamily: string;
    fontSizePx: number | null;
    linkColor: string;
    outerBorderColor: string;
    outerBorderWidthPx: number;
    rowsBorderWidthPx: number;
    selectableText: boolean;
    tdBorderColor: string;
    thBorderColor: string;
    thEvenBackground: string;
    thEvenColor: string;
    thOddBackground: string;
    thOddColor: string;
    trEvenBackground: string;
    trEvenColor: string;
    trOddBackground: string;
    trOddColor: string;
}

// @public
export function useHtmlTableProps({ key, style, tnode }: CustomTagRendererProps<TBlock>, tableConfig?: TableConfig): HTMLTableProps & {
    key?: string | number;
};


// (No @packageDocumentation comment for this package)

```