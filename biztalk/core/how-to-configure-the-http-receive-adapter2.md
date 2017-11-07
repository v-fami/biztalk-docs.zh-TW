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
ms.openlocfilehash: ed6e40036308aa872a2d6ba23da8209ee9f80cfc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
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
 [在配接器的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)