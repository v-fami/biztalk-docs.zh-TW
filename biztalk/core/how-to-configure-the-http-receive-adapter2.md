---
title: "如何設定 HTTP 接收 Adapter2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP receive adapter, configuring
- configuring HTTP receive adapter
ms.assetid: dd26fd57-90d8-4ffe-b56f-8de55ecc6f68
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c39e55ca233ef9875d3d56d25312ef879e3c539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a>如何設定 HTTP 接收配接器
您可以使用 HTTP 接收配接器，將訊息提交至 BizTalk Server。 HTTP 接收配接器是裝載於 IIS 程序中的 Internet Information Services (IIS) ISAPI 延伸模組。  
  
### <a name="to-configure-the-http-receive-adapter"></a>若要設定 HTTP 接收配接器  
  
1.  將 HTTP 接收配接器 (BTSHTTPReceive.dll) 從 **\<BizTalk2010 > \HttpReceive >**包含單一登入 (SSO) 專案的資料夾 (例如， **< Adapter_install > \biztalk2010\SSO\mySSODemo**)。  
  
    1.  新增網頁服務延伸模組 mySSODemo。  
  
    2.  瀏覽至 <BizTalk_install>\HttpReceive，然後將其中的 HTTP 接收配接器複製到您的 SSO 專案所在的資料夾，例如，  
  
         <Adapter_install>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll。  
  
    3.  將 mySSODemo 網頁服務延伸的狀態**允許**。  
  
2.  重新啟動 IIS 以確定所有變更均生效。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on3.md)