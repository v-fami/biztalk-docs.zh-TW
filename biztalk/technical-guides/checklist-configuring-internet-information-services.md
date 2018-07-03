---
title: 檢查清單： 設定 Internet Information Services |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 186f82c0-bd50-4c79-a403-8b0d91cc68d6
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c9cddbec30bb1dd7953ec30cfd9915e6d87a791
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007519"
---
# <a name="checklist-configuring-internet-information-services"></a>檢查清單： 設定 Internet Information Services
本主題列出準備在生產環境中使用 Internet Information Services (IIS) 時，應遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  


|                                                                                                                                                     步驟                                                                                                                                                      |                                                                                                                                                                                                                        參考                                                                                                                                                                                                                        |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                     設定 IIS 來發佈[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務                                                                                     |                                   -請參閱[「 啟用 Web 服務 」](http://go.microsoft.com/fwlink/?LinkId=153335) (<http://go.microsoft.com/fwlink/?LinkId=153335>) 中的 BizTalk Server 文件。<br />-請參閱[< 設定 IIS 的外掛式 WCF 接收配接器 >](http://go.microsoft.com/fwlink/?LinkId=202825)(<http://go.microsoft.com/fwlink/?LinkId=202825>) 中的 BizTalk Server 文件。                                   |
|                                                                              確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務是否正常運作。                                                                               | -請參閱[「 測試已發佈 Web 服務 」](http://go.microsoft.com/fwlink/?LinkId=153336) (<http://go.microsoft.com/fwlink/?LinkId=153336>) 中的 BizTalk Server 文件。<br />-請參閱["方式來建立.NET 應用程式來測試 WCF 服務發佈與 BizTalk WCF 服務發佈精靈 」](http://go.microsoft.com/fwlink/?LinkId=202830) (<http://go.microsoft.com/fwlink/?LinkId=202830>) 中的 BizTalk Server 文件。 |
|                            鎖定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務：<br /><br /> -關閉偵錯參數，在 web.config 或 machine.config 檔案中。<br />-設定使文章為唯一允許的動詞命令。                            |                        -請參閱 Microsoft 知識庫文章 815145， ["如何： 鎖定的 ASP.NET Web 應用程式或 Web 服務 」](http://go.microsoft.com/fwlink/?LinkId=153337) (<http://go.microsoft.com/fwlink/?LinkId=153337>)。<br />-請參閱[「 ASP.NET 編輯規則對話方塊 」](http://go.microsoft.com/fwlink/?LinkID=64566) (<http://go.microsoft.com/fwlink/?LinkID=64566>).NET Framework 2.0 文件中。                         |
|                                                                                      設定負載平衡使用 NLB （或其他負載平衡器） 在 BizTalk Server Web 服務和 WCF 服務之間平衡負載。                                                                                       |             -   **適用於 Windows Server 2008**： 請參閱 < [「 網路負載平衡部署指南 」](http://go.microsoft.com/fwlink/?LinkId=153139) (<http://go.microsoft.com/fwlink/?LinkId=153139>)。<br />-   **適用於 Windows Server 2003**： 請參閱 < [「 網路負載平衡： 適用於 Windows 2000 和 Windows Server 2003 的組態最佳作法 」](http://go.microsoft.com/fwlink/?LinkID=69529) (<http://go.microsoft.com/fwlink/?LinkID=69529>)。              |
| 變更 IIS 和 ASP.NET 設定調整 Web 服務。 **注意︰** ASP.NET 2.0 包含自動調整，因此，修改這些設定應該不需要針對 ASP.NET 2.0 網站中啟用自動設定的位置的 web.config 檔案\<processModel\>一節。 「 autoConfig = true"是預設設定。 |                                                                         檢閱 「 ASP.NET 設定，可能會影響 HTTP 或 SOAP 配接器的效能 > 主題的章節[」 組態參數，會影響配接器效能 >](http://go.microsoft.com/fwlink/?LinkId=153338) (<http://go.microsoft.com/fwlink/?LinkId=153338>) 中的 BizTalk Server 文件。                                                                          |
|                                                                             實作的方法發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務。                                                                             |                                                           -請參閱[網際網路對向 Web 服務和 WCF 服務發佈](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)。<br />-請參閱[< 發行 WCF 服務 >](http://go.microsoft.com/fwlink/?LinkId=202827) (<http://go.microsoft.com/fwlink/?LinkId=202827>) 中的 BizTalk Server 文件。                                                           |
|                                                                                                                             請依照下列最佳化 IIS 效能的最佳作法。                                                                                                                              |                                                                                                                                                    請參閱["的前十個辦法幫浦 IIS 效能 」](http://go.microsoft.com/fwlink/?LinkId=109107) (<http://go.microsoft.com/fwlink/?LinkId=109107>)。                                                                                                                                                    |
|                                                                                                                  請遵循最佳作法撰寫高效能適用於 IIS 的 web 應用程式。                                                                                                                  |                                                                                                                                              請參閱[「 10 個祕訣撰寫高效能 Web 應用程式 」](http://go.microsoft.com/fwlink/?LinkId=98290) (<http://go.microsoft.com/fwlink/?LinkId=98290>)。                                                                                                                                              |

## <a name="in-this-section"></a>本節內容  

-   [發佈網際網路對向 Web 服務和 WCF 服務](../technical-guides/publishing-internet-facing-web-services-and-wcf-services.md)