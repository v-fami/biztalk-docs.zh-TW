---
title: "轉換，並將訊息路由至磁碟資料夾、 佇列或 FTP 資料夾 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bfdbc38-6663-4d95-a0ed-57fec0245b9f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eb767b588f5531e033ec0c867ee2c6dfad02bc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transforming-and-routing-a-message-to-disk-folder-queue-or-ftp-folder"></a>轉換，並將訊息路由至磁碟資料夾、 佇列或 FTP 資料夾
在此使用案例中，ESB 轉換提交透過路線 Web 服務或任何上手的訊息。 動態解析查閱是 FILE 類型、 FTP 或佇列位置決定地圖名稱 （轉換） 以及訊息的目標端點，如圖 1 所示。  
  
 ![轉換磁碟資料夾](../esb-toolkit/media/ch3-transformingdiskfolder.gif "Ch3 TransformingDiskFolder")  
  
 **圖 1**  
  
 **轉換，並將訊息路由至磁碟資料夾**  
  
 動態解析 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它示範如何使用動態解析端點位置、 設定路由的屬性，並解決與執行元件[!INCLUDE[prague](../includes/prague-md.md)]對應在訊息層級，而不需使用協調流程。 它也示範單向和雙向的訊息模式。  
  
 此使用案例的延伸模組是轉換的簡單的路由解決方案將內送訊息路由至檔案、 FTP 或沒有其他步驟的佇列位置。  
  
 如需詳細資訊，請參閱[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)。