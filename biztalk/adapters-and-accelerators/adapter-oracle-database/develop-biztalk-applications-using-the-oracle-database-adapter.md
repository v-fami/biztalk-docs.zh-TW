---
title: "開發 BizTalk 應用程式使用 Oracle 資料庫配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Content-Based Routing (CBR)
- BizTalk orchestrations, using orchestrations to perform operations
ms.assetid: 65689c83-4a57-4aad-b0e9-f1bad901a7b9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1b3f688987c0c8339a2fd81c1b1ddf67128818
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-oracle-database-adapter"></a>開發 BizTalk 應用程式使用 Oracle 資料庫配接器
建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 XML 結構描述。 一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。  
  
 CBR 可用在案例中傳送給 Oracle 資料庫的訊息不需要任何大量的處理。 比方說，如果您知道接收埠會接收僅特定類型的訊息，您可以加入篩選條件要比對篩選條件運算式至傳送埠將訊息路由傳送埠。  
  
 在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 本節提供使用 BizTalk 協調流程對 Oracle 資料庫使用執行作業的相關資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它可以與 WCF 繫結互動。  
  
> [!IMPORTANT]
>  若要使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。 如需有關如何設定繫結屬性的指示，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!IMPORTANT]
>  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未列在 BizTalk Server 管理主控台。 中的配接器[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是 WCF 為基礎，並使用 WCF 自訂繫結。 BizTalk Server 管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。 它不會自動顯示 WCF 自訂繫結，並因此不會顯示 WCF 架構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
> 
> 此外，若要產生中繼資料，請使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。 請勿使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 如需使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。 
> 
> 針對其他配接器版本之間的差異，請參閱[移轉 BizTalk 專案建立使用 Oracle 資料庫的 BizTalk ODBC 配接器](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。  
  
  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)