# FrostRX_Heavy
用法：

RXIndex rxId = new RXIndex();

FrostRX.Instance.StartRX().ExecuteWhen(() => {text.text = _noticeQueue.Dequeue();group.blocksRaycasts=true;},

		()=>{return _noticeQueue.Count!=0;}).
		
		ExecuteUntil(()=>{group.alpha = Mathf.Lerp(group.alpha,1.2f,4.0f*Time.deltaTime);},()=>{return group.alpha>=1.0f;}).
		
		Wait(1.0f).
		
		ExecuteUntil(()=>{group.alpha = Mathf.Lerp(group.alpha,-0.2f,4.0f*Time.deltaTime);},()=>{return group.alpha<=0.0f;}).
		
		Execute(()=>{group.blocksRaycasts=false;}).
		
		GoToBegin().GetId(rxid);
    
    结束后会自动将rxid置为-1，适合rxid用的比较多的情况
