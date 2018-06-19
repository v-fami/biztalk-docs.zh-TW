---
title: Windows SharePoint Services 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41583fde-530a-4070-9647-f1ab6273aadf
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1af70299f5e308d1fc40fa6206f0ebfabff22a06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973284"
---
# <a name="windows-sharepoint-services-adapter-performance-counters"></a>Windows SharePoint Services 配接器效能計數器
效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下列效能計數器會在每個主控件執行個體可存取**biztalk: Windows Sharepoint Services 配接器**效能物件類別：  
  
|**類別目錄**|**計數器**|**說明**|  
|------------------|-----------------|---------------------|  
|BizTalk:Windows Sharepoint Services 配接器|% 接收訊息失敗|BizTalk Server 因為接收發生錯誤而尚未處理的 Windows SharePoint Services 檔案百分比。|  
||% 傳送訊息失敗|BizTalk Server 嘗試傳送至 Windows SharePoint Services 的失敗訊息百分比。|  
||% Web 服務呼叫失敗|已經失敗的 Windows SharePoint Services 配接器 Web 服務呼叫百分比。|  
||接收認可失敗總數|更新 SharePoint 文件的狀態時，發生的 Windows SharePoint Services 錯誤的總數。|  
||接收訊息失敗總數|BizTalk Server 已收到但因為錯誤而尚未處理的 Windows SharePoint Services 檔案總數。|  
||已接收訊息總數|Windows SharePoint Services 配接器接收的 Windows SharePoint Services 檔案總數，包括無法處理的檔案。|  
||傳送訊息失敗總數|BizTalk Server 嘗試傳送到 Windows SharePoint Services 的失敗訊息總數。|  
||已傳送訊息總數|BizTalk Server 傳送到 Windows SharePoint Services 的訊息總數，包括無法處理的檔案。|  
||Web 服務呼叫失敗總數|已經失敗的 Windows SharePoint Services 配接器 Web 服務呼叫總數。|  
||每秒 Web 服務呼叫數目|每秒的 Windows SharePoint Services 配接器 Web 服務呼叫數目。|  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 使用下列步驟來存取效能計數器。  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Windows Sharepoint Services 配接器**效能計數器物件，然後選取要監視的計數器  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。