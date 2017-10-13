# Tables with fixed headers
I finally found a good solution to fix headers on a table...

The sass and html can be found below, I didn't fill the table out because I am lazy and I copied this from a different app, but you get the idea. I used this in conjunction with [bootstrap 4](http://getbootstrap.com/docs/4.0/getting-started/download/) and [create-react-app](https://github.com/facebookincubator/create-react-app), so I know that at least it is compatible with that.

[Original Stack Overflow Post I found](https://stackoverflow.com/a/37295525/2081635)

Sass:
```scss
.table-fixed-header {
  width: 100%;
  position: relative;
  overflow: hidden;
  .table-fixed-header-container {
    overflow-y: auto;
    margin-top: 50px;
    table {
      width: 100%;
      td, th {
        padding: 10px;
      }
      thead tr th {
        height: 0;
        line-height: 0;
        margin: 0;
        padding-top: 0;
        padding-bottom: 0;
        color: transparent;
        white-space: nowrap;
        div {
          position: absolute;
          color: #000;
          height: 50px;
          padding: 10px;
          margin-left: -10px;
          line-height: normal;
          width: 100%;
          z-index: 2;
          text-align: left;
          font-weight: bold;
          background: white;
          top: 0;
        }
      }
      tbody {
        padding-top: 50px;
      }
    }
    &::-webkit-scrollbar {
      -webkit-appearance: none;
      width: 10px;
    }

    &::-webkit-scrollbar-thumb {
      border-radius: 5px;
      background-color: rgba(0,0,0,0.5);
      -webkit-box-shadow: 0 0 1px rgba(255,255,255,0.5);
    }
  }
}
```
HTML:
```html
<div className="table-fixed-header">
  <div className="table-fixed-header-container">
    <table className="table">
      <thead>
        <tr>
          <th>
            <div>
              Column 1
            </div>
          </th>
          <th>
            <div>
              Column 2
            </div>
          </th>
            Column 3
          <th>
            <div>
            Price
            </div>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>
            Body Column 1
          </td>
          <td>
            Body Column 2
          </td>
          <td>
            Body Column 3
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
```
