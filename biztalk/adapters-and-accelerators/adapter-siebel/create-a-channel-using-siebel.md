---
title: "建立通道使用 Siebel |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel programming, creating a channel
- how to, create a channel
- creating a channel
ms.assetid: 5587cf51-7101-4035-b958-3fe070ba6252
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87524160550cfe84c5e7e94efba1e44bff20c6ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-channel-using-siebel"></a><span data-ttu-id="24f84-102">建立使用 Siebel 的通道</span><span class="sxs-lookup"><span data-stu-id="24f84-102">Create a channel using Siebel</span></span>
<span data-ttu-id="24f84-103">本節示範如何建立直接傳訊與 Siebel 提供和使用 XML 訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="24f84-103">This section demonstrates how to create a channel for direct messaging with Siebel by providing and consuming XML messages.</span></span>  
  
```  
//create a channel factory, capable of sending a request to Siebel and receiving a reply (IRequestChannel)  
IChannelFactory<IRequestChannel> factory = binding.BuildChannelFactory<IRequestChannel>(new BindingParameterCollection());  
  
//open factory  
factory.Open();  
  
//obtain a channel from the factory by specifying the address you want to connect to  
IRequestChannel irc = factory.CreateChannel(address);  
  
//open the channel  
irc.Open();  
  
//perform operations  
…………  
…………  
…………  
  
//close the channel  
irc.Close();  
  
//close the factory  
factory.Close();  
```  
  
 <span data-ttu-id="24f84-104">當您建立通道之後時，您可以使用該通道在 Siebel 上執行作業。</span><span class="sxs-lookup"><span data-stu-id="24f84-104">Once you have created the channel, you can use that channel to perform operations on Siebel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f84-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24f84-105">See Also</span></span>  
 <span data-ttu-id="24f84-106">[開發 Siebel 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md) </span><span class="sxs-lookup"><span data-stu-id="24f84-106">[Develop Siebel Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md) </span></span>  
 [<span data-ttu-id="24f84-107">使用 Siebel 配接器使用 WCF 通道模型執行商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="24f84-107">Run Operations on Business Components with the Siebel adapter using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md)