<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [@digitalpersona/devices](./devices.md) &gt; [WindowsAuthClient](./devices.windowsauthclient.md) &gt; [on](./devices.windowsauthclient.on.md)

## WindowsAuthClient.on() method

Adds an event handler for the event. This is a multicast subscription, i.e. many handlers can be registered at once.

<b>Signature:</b>

```typescript
on<E extends Event>(event: string, handler: Handler<E>): Handler<E>;
```

## Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  event | <code>string</code> | a name of the event to subscribe, e.g. "CommunicationFailed" |
|  handler | <code>Handler&lt;E&gt;</code> | an event handler. |

<b>Returns:</b>

`Handler<E>`

an event handler reference. Store the reference and pass it to the [WindowsAuthClient.off()](./devices.windowsauthclient.off.md) to unsubscribe from the event.

## Example


```
class IntegratedWindowsAuthComponent
{
    private client: WindowsAuthClient;

    private onCommunicationFailed = (event: CommunicationFailed) => { ... }

    public $onInit() {
        this.client = new WindowsAuthClient();
        this.client.on("CommunicationFailed", this.onCommunicationFailed);
    }
    public $onDestroy() {
        this.client.off("CommunicationFailed", this.onCommunicationFailed);
        // alternatively, call this.reader.off() to unsubscribe from all events at once.
        delete this.client;
    }
}

```

