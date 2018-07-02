---
title: HTTP 配接器範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: 6796ea39-2947-45df-b228-1ecdb23a7ab8
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7682a16bd298ed58cf55e5122603bb2b3af9003
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977967"
---
# <a name="http-adapter-samples"></a>HTTP 配接器範例
本節包含的範例將示範使用 BizTalk HTTP 配接器時可使用的進階功能。  
  
> [!NOTE]
>  執行此範例之前，您必須執行下列步驟：  
> 
> 1. 開啟 IIS、加入 ISAPI 及 CGI 限制：  
> 
>    按一下左面板上的 [機器名稱]，再按一下右面板上的 [ISAPI 及 CGI 限制]，然後按一下 [加入 ISAPI 或 CGI 路徑]：  
> 
>    在 64 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\HttpReceive64\BTSHTTPReceive.dll  
> 
>    在 32 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\HttpReceive\BTSHTTPReceive.dll  
> 
>    檢查允許的延伸模組路徑或執行。  
>    2.  按一下左面板上的 [HTTPRequestResponseSample]，再按一下中間面板上的 [處理常式對應]，然後按一下具有下列設定的 [新增指令碼對應]：  
> 
>    要求路徑：BTSHTTPReceive.dll  
> 
>    可執行檔：  
> 
>    在 64 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\HttpReceive64\  
> 
>    在 32 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\HttpReceive\  
> 
>    要求的限制：  
> 
>    動詞： POST  
> 
>    存取：指令碼  
  
## <a name="in-this-section"></a>本節內容  
  
-   [HTTPSolicitResponse](../core/httpsolicitresponse.md)  
  
-   [HTTPRequestResponse](../core/httprequestresponse.md)