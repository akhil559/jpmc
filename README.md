# jpmc

 import './App.css';

class App extends Component<{}, IState> {
     
       data: [],
     showGraph: false,
     };
   }
 
 class App extends Component<{}, IState> {
    
   renderGraph() {
    return (<Graph data={this.state.data}/>)
    if(this.state.showGraph) {
      return (<Graph data={this.state.data}/>)
    }
   }
 
   
   getDataFromServer() {
    DataStreamer.getData((serverResponds: ServerRespond[]) => {
     
      this.setState({ data: [...this.state.data, ...serverResponds] });
    });
    let x = 0;
    const interval = setInterval(() => {
      DataStreamer.getData((serverResponds: ServerRespond[]) => {
      
        this.setState ({
          data: serverResponds ,
          showGraph: true ,
        });
      });
      x++;
      if (x > 1000)
      {
        clearInterval(interval);
      } 
    }, 100);
   }
 
  

 import React, { Component } from 'react';
import { Table } from '@jpmorganchase/perspective';
import { Table } from '@finos/perspective';
 import { ServerRespond } from './DataStreamer';
 import './Graph.css';
 
 interface IProps {
  
interface PerspectiveViewerElement {
interface PerspectiveViewerElement extends HTMLElement{
   load: (table: Table) => void,
 }
 
class Graph extends Component<IProps, {}> {
 
   componentDidMount() {
    
    const elem: PerspectiveViewerElement = document.getElementsByTagName('perspective-viewer')[0] as unknown as PerspectiveViewerElement;
    const elem = document.getElementsByTagName('perspective-viewer')[0] as unknown as PerspectiveViewerElement;
 
     const schema = {
       stock: 'string',
class Graph extends Component<IProps, {}> {
 
      elem.load(this.table);
      elem.setAttribute('view', 'y_line');
      elem.setAttribute('column-pivots', '["stock"]');
      elem.setAttribute('row-pivots', '["timestamp"]');
      elem.setAttribute('columns','["top_ask_price"]');
      elem.setAttribute('aggregates', `
      {"stock": "discount count",
      "top_ask_price":"avg",
      "top_bid_price": "avg",
      "timestamp":"distinct count"}`)
     }
   }
