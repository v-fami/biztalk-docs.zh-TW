---
title: 開發 BizTalk 應用程式使用 Oracle 資料庫配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Content-Based Routing (CBR)
- BizTalk orchestrations, using orchestrations to perform operations
ms.assetid: 65689c83-4a57-4aad-b0e9-f1bad901a7b9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05b342de0cb2bf7d99cf50774bedb81f36f82d9c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002359"
---
# <a name="develop-biztalk-applications-using-the-oracle-database-adapter"></a>開發 BizTalk 應用程式使用 Oracle 資料庫配接器
開發 BizTalk 應用程式牽涉到建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 XML 結構描述。 一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程來傳送和接收符合產生的結構描述的訊息。  
  
 CBR 可用在案例中傳送到 Oracle 資料庫的訊息不需要任何大量的處理。 例如，如果您知道只有特定類型的訊息將接收的接收埠，您可以加入篩選條件要比對傳送埠的篩選運算式將訊息路由的傳送埠。  
  
 在 BizTalk 協調流程中，建立傳送和接收埠以傳送和接收訊息，來回[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，其接著會將傳送訊息至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 本節提供使用 BizTalk 協調流程上使用您建立 Oracle 資料庫執行作業的相關資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接著會使用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它可以與 WCF 繫結互動。  
  
> [!IMPORTANT]
>  若要使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**繫結屬性**True**。 如需有關如何設定繫結屬性的相關指示，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
> 
> [!IMPORTANT]
>  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未列在 BizTalk Server 管理主控台。 中的配接器[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是以 WCF 為基礎，並使用 WCF 自訂繫結。 BizTalk Server 管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。 它不會自動顯示 WCF 自訂繫結，並因此不會顯示 WCF 架構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
> 
> 此外，若要產生的中繼資料，請使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。 請勿使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 如需使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱 <<c2> [ 取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。 
> 
> 如需其他配接器版本之間的差異，請參閱[移轉 BizTalk 專案建立使用 BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。  
  
  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)