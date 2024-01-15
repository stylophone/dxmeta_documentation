# Message Center API

### 发送Req/Ack消息

`
MessageCenter.Instance.SendMessage(MessageDef msgDef, IMessage msg, Action<IMessage> callback, bool autoRemoveCallback = true);
`

用于发送C2S/S2C消息（可靠消息机制），MessageDef和IMessage只能传入C2S类型，举例：

```
MessageCenter.Instance.SendMessage(MessageDef.C2SDceHeartBeat, new DceHeartBeat(), (response) =>
{
    Debug.Log(response);
});
```


### 发送Fire-And-Forget消息

用于发送即发即忘消息，无回调，只接收C2S类型

`MessageCenter.Instance.JustSend(MessageDef msgDef, IMessage msg);`

用于发送C2S only消息

### 注册消息监听

主要用于注册notify (s2c)消息监听

`
MessageCenter.Instance.AddListener<T>(MessageDef msgDef, Action<IMessage> callback, bool autoRemoveCallback = false)
`

### 移除消息监听

`
MessageCenter.Instance.RemoveListener(MessageDef msgDef, Action<IMessage> callback)
`
