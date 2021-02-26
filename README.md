# Custom-Marker-on-Map-with-REACT_NATIVE

import React, { Component } from 'react';
import { View, Text, StyleSheet } from 'react-native';
import MapView, { Marker } from 'react-native-maps' 

export default class App extends Component {

  constructor(props) {
    super(props)
    this.state = {
      markers: [],
      cords: []
    }
  }

  setCords(e) {
    this.setState({ markers: [...this.state.markers, { data: e.nativeEvent.coordinate }], 
      cords: e.nativeEvent.coordinate },()=>{  console.log(this.state.cords)
      })
}
  render() {
    return (
      <MapView
        style={styles.MainContainer}
        initialRegion={{
          latitude: 20.766500,
          longitude: 72.969704,
          latitudeDelta: 0.0922,
          longitudeDelta: 0.0421
        }}
        onPress={(e) => this.setCords(e)}
      >
        {this.state.markers.map((marker, i) => (
          <MapView.Marker key={i} coordinate={marker.data} />
        ))}
      </MapView>
    );
  }
}

const styles = StyleSheet.create({

  MainContainer: {
    position: 'absolute',
    top: 0,
    left: 0,
    right: 0,
    bottom: 0,
    alignItems: 'center',
    justifyContent: 'flex-end',
  },
  mapStyle: {
    position: 'absolute',
    top: 0,
    left: 0,
    right: 0,
    bottom: 0,
  }
})
