---
title: 高效能 BizTalk 解決方案的檢測最佳做法 |Microsoft Docs
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
ms.openlocfilehash: 60faad9e9e2905da963ee911dc9d7f13a39d2c67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997463"
---
# <a name="instrumentation-best-practices-for-high-performance-biztalk-solutions"></a>高效能 BizTalk 解決方案的檢測最佳做法
若要下載這份文件的複本，請前往[ http://go.microsoft.com/fwlink/?LinkId=205874 ](http://go.microsoft.com/fwlink/?LinkId=205874)。  
  
 **發行日期：** 2010 年 11 月  
  
 **作者：** Valery Mizonov，Microsoft Corporation  
  
 **審稿者：**  
  
- Mark Simms，Microsoft Corporation  
  
- Jayanthi Sampathkumar，Microsoft Corporation  
  
- Krish Srinivasan，Microsoft Corporation  
  
  **適用對象：** Microsoft BizTalk Server  
  
  **摘要：** 檢測 BizTalk 解決方案的傳統方式不一定總是從效能觀點來看最有效。 常用的檢測和追蹤元件利用 Win32 偵錯 Api 可能會造成潛在的瓶頸，並也越來越有責任在多執行緒在壓力下執行的 BizTalk 應用程式的效能降低。  
  
  從另一端，來源的程式碼檢測提供相當大的可見性的應用程式行為，並有助於減少整體的疑難排解時。 因此，本質上新的方法來檢測高效能 BizTalk 解決方案已經成為十分重要，若要啟用非干擾式的方式，幾乎沒有任何額外負荷與不會影響收集的豐富且詳細的診斷資訊在 應用程式的效能。  
  
  [Windows Server AppFabric 客戶諮詢小組](http://blogs.msdn.com/appfabriccat)microsoft 為了社群提供已驗證的最佳作法可協助 BizTalk 開發人員擴充其解決方案的高效能檢測在內部採用許多的 Microsoft 產品。 這些最佳作法有尚未反映這些可重複使用的架構 BizTalk 開發人員可以輕鬆地插入和在自己的實作中採用的形式。  
  
  您可以下載的完整副本[高效能 BizTalk 解決方案的檢測最佳做法](http://go.microsoft.com/fwlink/?LinkId=205874)(http://go.microsoft.com/fwlink/?LinkId=205874) Microsoft Download Center 上。