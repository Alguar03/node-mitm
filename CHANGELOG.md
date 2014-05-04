## Unreleased
- Adds support for Node v0.10.24 and up.
- Adds the `connection` event to Mitm to get the remote `Net.Socket`. You can
  use this to intercept and test any TCP code.  
  If you need the client side socket for any reason, listen to `connect` on
  Mitm.

- Replaces the `ClientRequest` given to the `request` event on Mitm
  with a proper `IncomingMessage` — just like a regular Node server would
  receive.  
  This ensures the requests you make are properly parseable according to HTTP
  specs (assuming Node.js itself is implemented according to spec) and also lets
  you assert on the content of `POST` requests.

  ```javascript
  var mitm = Mitm()
  Http.request({host: "x.org"}).end()
  mitm.on("request", function(req) { req.headers.host.must.equal("x.org") })
  ```

## 0.3.0 (Apr 26, 2014)
- Adds support for calling `Net.connect` with `port` and `host` arguments.

## 0.2.0 (Apr 19, 2014)
- Does not store requests on an instance of `Mitm` any longer.
- Adds `socket` event to `Mitm`.
- Updated to work with Node v0.11.12.

## 0.1.337 (Mar 11, 2014)
- First private release.
