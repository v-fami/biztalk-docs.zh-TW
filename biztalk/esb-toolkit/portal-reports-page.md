---
title: 入口網站報告頁面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51d793cc-dcea-4c29-883b-a5045d39d4f6
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a487f30fc4ca9897cfd1dc4642c26a2e5f36fd7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016769"
---
# <a name="portal-reports-page"></a>入口網站的報表 頁面
入口網站的報表頁面上，[圖 1] 所示，會顯示下列圖表：  

- **應用程式的錯誤計數**。 此選項會顯示在指定時間內產生的一組指定的應用程式的所有錯誤的彙總檢視。  

- **依錯誤類型的錯誤計數**。 此選項會依指定的錯誤類型經過一段指定時間產生的一組指定的應用程式中顯示彙總檢視的所有錯誤。  

- **不同時間的錯誤計數**。 這個選項會顯示為一組指定的應用程式在指定期間內的錯誤計數。 您可以選取要顯示的趨勢圖，顯示經過一段時間的應用程式內的特定服務的錯誤數目的應用程式。  

- **警示由應用程式的計數**。 此選項會顯示在指定時間內產生的一組指定的應用程式的所有警示彙總檢視。  

- **經過一段時間的 resubmissions**。 這個選項會顯示為一組指定的應用程式在指定期間內失敗的訊息 resubmissions 的計數。  

- **警示訂閱經過一段時間**。 此選項會顯示警示的訂用帳戶的計數為一組指定的應用程式在指定期間內。  

  ![入口網站報告頁面](../esb-toolkit/media/portalreportspage.gif "PortalReportsPage")  

  **圖 1**  

  **ESB 管理入口網站報告頁面**  

  下列清單說明如何使用 ESB 管理入口網站新登錄項目頁面的功能：  

- 按一下  **SelectApplications**連結上方的第一個圖表，然後選取或清除核取方塊會顯示已安裝 Microsoft BizTalk Server 應用程式清單中。 您也可以使用以選取 所有 或 無應用程式顯示的連結。 按一下 **儲存**以顯示所選的應用程式的資訊，或按一下**取消**放棄變更。  

- 使用第一個圖表上方的下拉式清單，選取您想要的圖表以顯示資料的間隔。 您可以選擇要包含資料的先前**小時、 天、 週、 月、 季、 年度**或是**所有**。  

- 按一下其中一個頁面，即可在應用程式中的服務所顯示的資料分析中的圖表。 根據圖表選取，這會顯示個別錯誤、 警示、 錯誤類型、 resubmissions 或警示的訂用帳戶每個服務的計數或趨勢線。  

- 按一下此圖表顯示一個表格，列出所有錯誤、 警示、 錯誤類型、 resubmissions 或針對選取的服務警示的訂用帳戶中的服務名稱。  

- 按一下 **匯出至 Excel**下載訂用帳戶中的格式，您可以在 Microsoft Excel 中檢視的清單。
