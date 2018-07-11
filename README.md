# React Native Event Calendar
A React Native iOS style calendar implemented using VirtualizedList.
This package now incorporates the work of https://github.com/duyluonglc/
who kindly added some featues and improvements.

## Demo
<img src="https://raw.githubusercontent.com/joshyhargreaves/react-native-event-calendar/master/demo/screenshot.png" width="360">

## Current API
Property | Type | Description
------------ | ------------- | -------------
onRef | PropTypes.function | Function fired to set the EventCalendar ref
events | PropTypes.array | Array of event
width | PropTypes.number | Container width
format24h | PropTypes.boolean | Use format 24hour or 12hour
formatHeader | PropTypes.string | Header date format
upperCaseHeader | PropTypes.boolean | Sets date header as uppercase (default false)
headerStyle | PropTypes.object | Header style
renderEvent | PropTypes.function | Function return a component to render event `renderEvent={(event) => <Text>{event.title}</Text>}`
eventTapped | PropTypes.function | Function on event press
dateChanged | PropTypes.function | Function on date change. Passes new date as a string formatted as 'YYYY-MM-DD'
initDate | PropTypes.string | Show initial date (default is today)
scrollToFirst | PropTypes.boolean | Scroll to first event of the day (default true)
size | PropTypes.number | Number of date will render before and after initDate (default is 30 will render 30 day before initDate and 29 day after initDate)
virtualizedListProps | PropTypes.object | Prop pass to virtualizedList
start | PropTypes.number | Start time (default 0)
headerIconLeft | PropTypes.element | If specified, renders this element instead of the default left arrow image
headerIconRight | PropTypes.element | If specified, renders this element instead of the default right arrow image
_goToDate | (date : string) => void | Requires the reference set using the `onRef` prop. E.g. `ref._goToDate('2017-09-07')`

`EventCalendar` can be configured through a `styles` prop whereby any of the components in the calendar can be styled.
```
    {
        container: {
            backgroundColor: 'white'
        }, 
        event: {
            opacity: 0.5
        }
    }
```

## Install
`npm i --save react-native-events-calendar`

## Examples
See Examples dir. 

```js
import EventCalendar from 'react-native-events-calendar'

let { width } = Dimensions.get('window')

const events = [
    { start: '2017-09-07 00:30:00', end: '2017-09-07 01:30:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-07 01:30:00', end: '2017-09-07 02:20:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-07 04:10:00', end: '2017-09-07 04:40:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-07 01:05:00', end: '2017-09-07 01:45:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-07 14:30:00', end: '2017-09-07 16:30:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-08 01:20:00', end: '2017-09-08 02:20:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-08 04:10:00', end: '2017-09-08 04:40:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-08 00:45:00', end: '2017-09-08 01:45:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-08 11:30:00', end: '2017-09-08 12:30:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-09 01:30:00', end: '2017-09-09 02:00:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-09 03:10:00', end: '2017-09-09 03:40:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' },
    { start: '2017-09-09 00:10:00', end: '2017-09-09 01:45:00', title: 'Dr. Mariana Joseph', summary: '3412 Piedmont Rd NE, GA 3032' }
]


render () {
  return (
    <EventCalendar
      eventTapped={this._eventTapped.bind(this)}
      events={this.state.events}
      width={width}
      initDate={'2017-09-08'}
    />
  )
}

```
