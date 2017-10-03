---
title: "疑難排解非-WCF 線條的商務配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d5f7877-656f-406e-9edb-d6b9a0705b02
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba36ed8a8efb62e2eb8e885791c3c28012dcc49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-non-wcf-line-of-business-adapters"></a>疑難排解非 WCF 商務營運系統配接器
## <a name="failed-to-retrieve-error"></a>「無法擷取」錯誤  
 使用非 WCF 企業營運 (LOB) 配接器時，可能發生下列錯誤：  
  
-   無法擷取系統  
  
-   瀏覽代理程式： 錯誤受困於建構函式。 目標電腦主動拒絕連線。  
  
-   執行階段代理程式： 錯誤受困於建構函式。 目標電腦主動拒絕連線。  
  
### <a name="cause"></a>原因  
 LOB 配接器使用 .Net 遠端處理。 如果 .Net 遠端處理的啟用時間比預期長，配接器便可能傳回這些錯誤。  
  
### <a name="resolution"></a>解決方案  
 建立**StartAgentSleep**登錄機碼，增加逾時值：  
  
1.  開啟登錄，並移至*HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*。  
  
2.  以下列屬性建立新的 DWORD 值：  
  
     名稱： StartAgentSleep  
  
     基底： 十進位  
  
     值資料： 1000年  
  
 屬值資料的單位是毫秒 (ms)。 1000ms 等於 1 秒。  
  
 在某些系統中，1 秒可能不夠。 增加該值並進行測試，有助於決定所需的適當逾時。  
  
> [!IMPORTANT]
>  加入**StartAgentSleep**登錄機碼將影響**所有**非 WCF LOB 配接器。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 BizTalk Server 配接器](../core/troubleshooting-biztalk-server-adapters.md)