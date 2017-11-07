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
ms.openlocfilehash: d6356a130b412ea849c79213ab55b000ea827f3a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
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
 [保護配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)