---
title: ESB 管理入口網站及錯誤訊息檢視器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4a1636c-2e45-4ee5-92c2-81c976582da3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9a6e7272e7b707b6ba7650cfb93506c3a54a00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295206"
---
# <a name="the-esb-management-portal-and-fault-message-viewer"></a>ESB 管理入口網站及錯誤訊息檢視器
主要元件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是網頁型入口網站提供的各種不同的例外狀況管理和警示通知功能; 此外，它會充當有用的組態管理 」 和 「 通用描述、 探索與整合 （UDDI) 登錄介面。 圖 1 顯示首頁的入口網站提供目前正在執行的應用程式的健全狀況的概觀。  
  
 ![入口網站首頁](../esb-toolkit/media/portalhomepage.gif "PortalHomePage")  
  
 **圖 1**  
  
 **ESB 管理入口網站的 [首頁]**  
  
 使用者可以選取的錯誤訊息顯示在 ESB 管理入口網站中檢視錯誤的環境和靜態屬性和錯誤訊息中包含的原始訊息的清單，如圖 2 所示。  
  
 ![錯誤檢視器頁面](../esb-toolkit/media/ch4-faultviewerpage.gif "第 4 章第 FaultViewerPage")  
  
 **圖 2**  
  
 **ESB 管理入口網站的 ESB 錯誤檢視器 頁面**  
  
 ESB 管理入口網站中顯示的 ESB 錯誤訊息可能會處理送出時，原始訊息的值發生錯誤的結果。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援 「 修復和重新送出 」 功能，可讓系統管理員或使用者編輯失敗的訊息，並將其發行到上手進行處理。  
  
 選取其中一個包含的訊息會開啟 [訊息] 檢視頁面在訊息詳細資料檢視中，如圖 3 所示。 在這個檢視中，使用者可以看見訊息內容，請下載郵件，或按一下**編輯**切換到編輯檢視中，他們可以在其中修復和重新提交訊息。  
  
 ![訊息檢視器頁面](../esb-toolkit/media/ch4-messageviewerpage.gif "第 4 章第 MessageViewerPage")  
  
 **圖 3**  
  
 **ESB 訊息檢視器顯示的錯誤詳細資料檢視**  
  
 如需完整說明和 ESB 管理入口網站中，包括錯誤檢視器、 訊息重新提交程序，以及用於清單中，技術的使用方式選項排序和分析錯誤，請參閱[BizTalk ESB 的管理Toolkit](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)。