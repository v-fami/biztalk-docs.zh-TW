---
title: 如何建立或新增成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, creating
- applications, artifacts
ms.assetid: fea7487c-b5fa-457f-8c74-a20ea3a6df85
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b231cdf6a25c4ca316c9620ee789e6e3a715fd6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249486"
---
# <a name="how-to-create-or-add-an-artifact"></a>如何建立或新增成品
在建立 BizTalk 應用程式之後，可以從檔案系統新增以檔案為基礎的成品 (例如，BizTalk 組件、.NET 組件、指令碼和憑證)，或從「規則引擎」資料庫新增原則。 也可以在應用程式內建立傳送埠、傳送埠群組、接收位置和接收埠。 建立或新增成品會將成品新增至 BizTalk 管理資料庫。 然後您可以部署應用程式和其成品當做單一實體中所述[部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)。  
  
> [!NOTE]
>  BizTalk 應用程式或群組中的某些類型成品必須是唯一的。 如需詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。  
  
 如需新增或建立每種成品類型的程序，請參閱下列主題：  
  
-   [如何建立傳送埠](../core/how-to-create-a-send-port2.md)  
  
-   [如何建立傳送埠群組](../core/how-to-create-a-send-port-group.md)  
  
-   [如何建立接收埠](../core/how-to-create-a-receive-port.md)  
  
-   [如何建立接收位置](../core/how-to-create-a-receive-location.md)  
  
-   [如何新增原則至應用程式](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [如何將檔案新增至應用程式](../core/how-to-add-a-file-to-an-application.md)  
  
-   [如何將憑證新增至應用程式](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [如何將 COM 元件新增至應用程式](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [如何將.NET 組件新增至應用程式](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [如何將 BAM 成品新增至應用程式](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
> [!NOTE]
>  如果您要加入的成品所在的路徑 (例如，路徑及檔案名稱) 太長，加入成品至應用程式的作業可能會失敗。 路徑不得超過 260 個字元。  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [如何將 64 位元成品新增至應用程式](../core/how-to-add-a-64-bit-artifact-to-an-application.md)