---
title: "Siebel 配接器用戶端功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- features, of the adapter
ms.assetid: 11792629-a692-4378-b522-d33484ee8acb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f929b14415265c4ad9894a16b87294dccd4e906f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-siebel-adapter-clients"></a>Siebel 配接器用戶端的功能
除了所有的主題所討論的功能[概觀的 BizTalk 配接器 for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)、[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供可用於配接器用戶端的下列功能：  
  
-   **設定配接器使用的繫結屬性的支援**。 可以設定配接器用戶端[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]藉由指定特定繫結內容產生中繼資料時。 如需詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
-   **作業參數的 null 值支援**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器用戶端提供的商務物件的作業參數使用 XSD 的"nillable"屬性的 null 值。 配接器並未通過 Siebel 系統具有 null 值的欄位。  
  
-   **支援 XML 資料流**。 配接器用戶端可以串流處理的資料或從[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用**XMLReader**或**XMLWriter**介面。  
  
-   **支援 BizTalk Server 中的動態連接埠**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱[使用 Siebel 配接器設定動態連接埠](../../adapters-and-accelerators/adapter-siebel/configure-dynamic-ports-with-the-siebel-adapter.md)。  
  
-   **訊息版本控制支援**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援訊息版本控制。 這可支援不同的訊息結構描述版本，後續的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[訊息版本控制支援](../../adapters-and-accelerators/adapter-siebel/message-versioning-support2.md)。  
  
-   **對效能計數器支援**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援配接器用戶端可以使用的 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱[Siebel 配接器使用效能計數器](../../adapters-and-accelerators/adapter-siebel/use-performance-counters-with-the-siebel-adapter.md)。  
  
    > [!NOTE]
    >  這項功能不提供與舊版配接器的回溯相容性。  
  
-   **XML 項目名稱編碼方式**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現從企業應用程式的實體當做 XML 中的項目名稱。 底線會是唯一的特殊字元可包含的元素名稱。 因此，底線用來編碼含有特殊字元的項目名稱。 例如，`emp$name`編碼為`emp_x0024_name`。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Siebel eBusiness 應用程式中的概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)