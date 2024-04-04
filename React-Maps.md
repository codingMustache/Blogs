test
## Version Information
  - Node v18
  - React-Mapbox-Gl v15
  - Mapbox-Gl v2

React-mapbox-gl is a library that allows you to use Mapbox GL JS, a JavaScript library for interactive, customizable vector maps, within a React application. It provides a set of React components that make it easy to work with Mapbox GL JS in a declarative way, by allowing you to specify the map's behavior and style as props on a React component.

To get started with react-mapbox-gl, you will need to have a Mapbox access token, which you can obtain by signing up for a Mapbox account. Once you have your access token, you can install the library using npm or yarn:

```sh
npm install react-mapbox-gl mapbox-gl
```

or

```sh
yarn add react-mapbox-gl mapbox-gl
```

Next, you can import the Map component from react-mapbox-gl and use it to render a map in your application:


```js
import React from 'react';
import MapboxGL from 'mapbox-gl';
import { Map } from 'react-mapbox-gl';
const App = () => {
  return (
    <Map
      style={{
        width: '100%',
        height: '100%',
      }}
      mapboxAccessToken={mapbox_token}
      initialViewState={{
        latitude: 29.935260993668,
        longitude: -90.08128396541,
        zoom: 12,
        pitch: 60,
      }}
      mapStyle='mapbox://styles/mapbox/light-v11'
    />
  );
};
export default App;
```

The Map component takes a number of props that allow you to customize the appearance and behavior of the map. For example, you can use the `mapStyle` prop to specify the Mapbox style to use for the map, and the center and zoom props to control the initial map view.

You can also add other Mapbox GL JS features to the map using the other components provided by react-mapbox-gl, such as Marker, Popup, and Layer. For example, you can add a marker to the map like this:

```js
import React, { useState } from 'react';
import MapboxGL from 'mapbox-gl';
import { Map, Marker } from 'react-mapbox-gl';

const App = () => {
  const [mark, setMark] = useState()
  const [showPopup, setShowPopup] = useState(false)

const {lat, lon} = mark
return (
    <Map
      style="mapbox://styles/mapbox/streets-v9"
      containerStyle={{
        height: '400px',
        width: '100%'
      }}
      center={[-74.50, 40]}
      zoom={9}
    >
    {/*
    based on the mark object the mark
    the popup will render conditionally
    */}
    {showPopup ?
      <Marker
        longitude={lon}
        latitude={lat}
        onClick={() => setShowPopup(false)}
      >
      </Marker>
    :
      <Popup
        longitude={lon}
        latitude={lat}
        anchor='bottom'
        closeOnClick={false}
        onClose={() => setShowPopup(true)}
        focusAfterOpen={true}
      >
      {/* popup info*/}
      </Popup>
    }
    </Map>
  );
};
export default App;
```

The Marker and the Popup component takes a coordinates prop that specifies the latitude and longitude of the marker, and you can add any content you want inside the Marker component to customize the appearance of the marker.

react-mapbox-gl also provides several other features that make it easy to work with Mapbox GL JS in a React application. For example, you can use the onStyleLoad prop to perform an action when the map style has finished loading, or use the onClick prop to handle click events on the map. You can find a full list of available props