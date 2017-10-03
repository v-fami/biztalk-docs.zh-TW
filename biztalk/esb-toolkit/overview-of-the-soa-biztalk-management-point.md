---
title: "SOA BizTalk 管理點的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4c3a30-c50e-4c1c-9f59-d9a364078388
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60f73834a9bc02e371d4050115b1eccf5e88e02f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-soa-biztalk-management-point"></a>SOA BizTalk 管理點的概觀
SOA 服務管理員和工作臺產品與原生整合，BizTalk 管理點。 不同於一般的 Web 服務管理點，這項實作都與 Microsoft BizTalk Server 環境，以表示 BizTalk Server 所提供的服務接收位置和傳送埠。 因為任意本質的接收位置和傳送埠 （針對各種不同的 BizTalk Server 配接器設定），這些服務不一定與 Web 服務相關聯，但它們可以被視為方面 SOA Service Manager 中的 Web 服務和 SOA Workbench。  
  
 圖 1 顯示 SOA 服務管理員 Web 應用程式顯示的範例應用程式的 [Workbench] 頁面。 左側的樹狀檢視可讓使用者瀏覽應用程式和服務安裝 BizTalk Server 中，右邊窗格可讓使用者檢視應用程式詳細資料、 作業、 存取連接埠、 類別、 規則和監視資訊。  
  
 ![Ch9 &#45;SOAServiceManager](../esb-toolkit/media/ch9-soaservicemanager.jpg "Ch9 SOAServiceManager")  
  
 **圖 1**  
  
 **SOA 服務管理員 [Workbench] 頁面上顯示可用的監視功能**  
  
 您可以監視所有作業，在應用程式 （所有傳送埠和接收位置） 或特定的作業。Workbench 通過所選的訊息清單會顯示傳送埠和接收位置。 當您按兩下清單中的訊息時，Workbench （如果已啟用記錄），就會顯示訊息和其內容屬性的詳細資料。 或者，您可以在通過該服務的即時訊息中選取特定的服務和監視。