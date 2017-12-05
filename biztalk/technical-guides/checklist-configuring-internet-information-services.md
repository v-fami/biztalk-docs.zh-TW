---
title: "檢查清單： 設定 Internet Information Services |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 186f82c0-bd50-4c79-a403-8b0d91cc68d6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24c2c0c97cb70dca268273d9ed5855f72372a2ca
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="checklist-configuring-internet-information-services"></a>檢查清單： 設定 Internet Information Services
本主題列出準備在生產環境中使用的網際網路資訊服務 (IIS) 時，應遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
|步驟|參考|  
|-----------|---------------|  
|設定 IIS 以發佈[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務|-了解[「 啟用 Web 服務 」](http://go.microsoft.com/fwlink/?LinkId=153335) (http://go.microsoft.com/fwlink/?LinkId=153335) 中的 BizTalk Server 文件。<br />-了解[「 設定 IIS 的外掛式 WCF 接收配接器 」](http://go.microsoft.com/fwlink/?LinkId=202825)(http://go.microsoft.com/fwlink/?LinkId=202825) 中的 BizTalk Server 文件。|  
|確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務是否正常運作。|-了解[「 測試已發佈 Web 服務 」](http://go.microsoft.com/fwlink/?LinkId=153336) (http://go.microsoft.com/fwlink/?LinkId=153336) 中的 BizTalk Server 文件。<br />-了解["方式來建立.NET 應用程式來測試 WCF 服務發佈與 BizTalk WCF 服務發佈精靈 」](http://go.microsoft.com/fwlink/?LinkId=202830) (http://go.microsoft.com/fwlink/?LinkId=202830) 中的 BizTalk Server 文件。|  
|鎖定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務：<br /><br /> -關閉偵錯參數，在 web.config 或 machine.config 檔案中。<br />-設定使 POST 為唯一允許的動詞命令。|-請參閱 Microsoft 知識庫文章 815145， ["如何： 鎖定的 ASP.NET Web 應用程式或 Web 服務"](http://go.microsoft.com/fwlink/?LinkId=153337) (http://go.microsoft.com/fwlink/?LinkId=153337)。<br />-了解["ASP.NET 編輯規則對話方塊 」](http://go.microsoft.com/fwlink/?LinkID=64566) (http://go.microsoft.com/fwlink/?LinkID=64566).NET Framework 2.0 文件中。|  
|設定負載平衡使用 NLB （或其他負載平衡器） 在 BizTalk Server Web 服務和 WCF 服務之間平衡負載。|-   **適用於 Windows Server 2008**： 請參閱[「 網路載入平衡部署指南 」](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139)。<br />-   **適用於 Windows Server 2003**： 請參閱[「 網路負載平衡： 最佳做法適用於 Windows 2000 和 Windows Server 2003"](http://go.microsoft.com/fwlink/?LinkID=69529) (http://go.microsoft.com/fwlink/?LinkID=69529)。|  
|變更 IIS 和 ASP.NET 設定調整 Web 服務。 **注意：** ASP.NET 2.0 包含自動調整，因此，修改這些設定應該不需要的自動設定會在中啟用 ASP.NET 2.0 Web 網站的 web.config 檔案\<processModel\> > 一節。 「 autoConfig = true"是預設值。|檢閱 < ASP.NET 設定，可能會影響 HTTP 或 SOAP 配接器的效能 > 主題的章節[」 組態參數，會影響配接器效能 」](http://go.microsoft.com/fwlink/?LinkId=153338) (http://go.microsoft.com/fwlink/?LinkId=153338) 中的 BizTalk Server 文件。|  
|實作的方法發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務。|-了解[網際網路對向 Web 服務和 WCF 服務發佈](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)。<br />-了解[「 發佈 WCF 服務 」](http://go.microsoft.com/fwlink/?LinkId=202827) (http://go.microsoft.com/fwlink/?LinkId=202827) 中的 BizTalk Server 文件。|  
|請依照 IIS 效能最佳化最佳的作法。|請參閱["Top 幫浦 IIS 效能十種"](http://go.microsoft.com/fwlink/?LinkId=109107) (http://go.microsoft.com/fwlink/?LinkId=109107)。|  
|請遵循最佳作法撰寫適用於 IIS 的 web 應用程式的高效能。|請參閱[「 10 撰寫高效能的秘訣 Web 應用程式 」](http://go.microsoft.com/fwlink/?LinkId=98290) (http://go.microsoft.com/fwlink/?LinkId=98290)。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [發佈網際網路對向 Web 服務和 WCF 服務](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)