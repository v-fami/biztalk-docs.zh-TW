---
title: 檢測的高效能的 BizTalk 解決方案的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd16ea1e-055a-429b-912f-bff2b91f0fdb
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ef6f243f894071aebb0089f063ed0242ee09d9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298518"
---
# <a name="instrumentation-best-practices-for-high-performance-biztalk-solutions"></a>檢測的高效能的 BizTalk 解決方案的最佳作法
若要下載這份文件的複本，請移至[http://go.microsoft.com/fwlink/?LinkId=205874](http://go.microsoft.com/fwlink/?LinkId=205874)。  
  
 **發行日期：** 2010 年 11 月  
  
 **作者：** Valery Mizonov，Microsoft Corporation  
  
 **審稿者：**  
  
-   Mark Simms，Microsoft Corporation  
  
-   Jayanthi Sampathkumar，Microsoft Corporation  
  
-   Krish Srinivasan，Microsoft Corporation  
  
 **適用於：** Microsoft BizTalk Server  
  
 **摘要：** 傳統的檢測 BizTalk 解決方案的方式可能永遠無法從效能觀點來看最有效。 常用的檢測和追蹤元件利用 Win32 偵錯 Api 可能會介紹潛在的瓶頸，並會變成負責多執行緒在壓力下執行的 BizTalk 應用程式中的效能降低。  
  
 從另一端，來源的程式碼檢測會提供很大的可見性的應用程式行為，而且有助於減少整體的疑難排解工作。 因此，基本上是新的方法檢測的高效能 BizTalk 解決方案變得少很重要，以啟用不會造成干擾的方式，使用幾乎任何額外負荷，不會影響收集的豐富且詳細的診斷資訊在應用程式的效能。  
  
 [Windows Server AppFabric 客戶諮詢團隊](http://blogs.msdn.com/appfabriccat)microsoft 社群提供已驗證的最佳做法的目標是協助 BizTalk 開發人員擴充與高效能檢測解決方案在內部採用許多 Microsoft 產品。 這些最佳作法已反映在可重複使用的架構的 BizTalk 開發人員可以輕鬆地插入並採用它們自己的實作中的表單。  
  
 您可以下載的完整副本[檢測的高效能的 BizTalk 解決方案的最佳作法](http://go.microsoft.com/fwlink/?LinkId=205874)(http://go.microsoft.com/fwlink/?LinkId=205874) 在 Microsoft Download Center 上。