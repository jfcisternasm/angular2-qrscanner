# angular2-qrscanner
QrScanner will scan for a QRCode from your Web-cam and return its
string representation by drawing the captured image onto a 2D Canvas
and use [@LazarSoft/jsqrcode](https://github.com/LazarSoft/jsqrcode) to check for a valid QRCode every *Xms*

### usage
```bash
$ npm install --save angular2-qrscanner
```

```typescript
// app.module.ts
import { QrScannerModule } from 'angular2-qrscanner';
@NgModule({
  declarations: [
    // ...
  ],
  imports: [
    // ...
    QrScannerModule,
  ],
  providers: [],
  bootstrap: [
    // ...
  ]
})
export class AppModule { }
```

```
<!-- app.component.html -->
<qr-scanner
  [debug]="false"        <!-- debug flag for console.log spam              (default: false) -->
  [canvasWidth]="640"    <!-- canvas width                                 (default: 640) -->
  [canvasHeight]="480"   <!-- canvas height                                (default: 480) -->
  [mirror]="false"       <!-- should the image be a mirror?                (default: false) -->
  [stopAfterScan]="true" <!-- should the scanner stop after first success? (default: true) -->
  [updateTime]="500"     <!-- miliseconds between new capture              (default: 500) -->
  [square]="true"        <!-- should the video be squared?                 (default: true) -->
  (onDeviceNotAllowed) = "showNotAllowMessage($event) <!-- User didn't give permissions or webcam don't exist -->
  (unSupportedBrowser) = "showNotSupportedBrowserMessage($event) <!-- Browser not supported -->
  (onRead)="decodedOutput($event)">
</qr-scanner>
```
```
@public
startScanning() {void}       Method called by ngInit to find devices and start scanning.
stopScanning() {void}        Method called by ngDestroy (or on successful qr-scan) to stop scanning

Both of these methods can be called to control the scanner if `stopAfterScan` is set to `false`
```
### source of my modifications for this fork
https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
