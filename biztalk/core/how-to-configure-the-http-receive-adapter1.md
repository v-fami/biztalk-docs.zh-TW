---
title: "如何設定 HTTP 接收 Adapter1 |Microsoft 文件"
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
ms.assetid: e7dbfed3-9dd8-49c9-90b6-a655d7c5446f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6907a96c3c961a4df7d076ba9307f44627bfa2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a>如何設定 HTTP 接收配接器
您可以使用 HTTP 接收配接器，將訊息提交至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 HTTP 接收配接器是裝載於 IIS 程序中的 Internet Information Services (IIS) ISAPI 延伸模組。  
  
### <a name="to-configure-the-http-receive-adapter"></a>若要設定 HTTP 接收配接器  
  
1.  將 HTTP 接收配接器 (BTSHTTPReceive.dll) 從 **\<BizTalk > \HttpReceive >**至資料夾包含您的單一登入 (SSO) 專案，例如：  
  
     **< Adapter_install > \biztalk\SSO\mySSODemo**  
  
    1.  新增網頁服務延伸模組 mySSODemo。  
  
    2.  找出並複製**< BizTalk_install > \HttpReceive**至資料夾包含您的 SSO 專案，例如：  
  
         **< Adapter_install > \biztalk\SSO\mySSODemo\BTSHTTPReceive.dll。**  
  
    3.  將 mySSODemo 網頁服務延伸狀態**允許**。  
  
2.  重新啟動 IIS 以套用所有變更。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on2.md)