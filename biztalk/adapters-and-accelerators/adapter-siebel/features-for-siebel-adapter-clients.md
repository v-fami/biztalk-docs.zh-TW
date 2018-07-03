---
title: Siebel 配接器用戶端的功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter features
- features, of the adapter
ms.assetid: 11792629-a692-4378-b522-d33484ee8acb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29d461b5ac656b9f3b84e58d0ecb2d4e6b5cff5d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004447"
---
# <a name="features-for-siebel-adapter-clients"></a>Siebel 配接器用戶端的功能
除了的主題所討論的功能之外[概觀的 BizTalk 配接器 for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)，則[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供適用於配接器用戶端的下列功能：  
  
- **設定使用繫結屬性的配接器支援**。 配接器用戶端可以設定[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]時產生的中繼資料指定特定繫結屬性。 如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
- **作業參數的 null 值支援**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器用戶端，以提供商務物件的作業參數使用 XSD 的"nillable"屬性的 null 值。 配接器不會通過 Siebel 系統具有 null 值的欄位。  
  
- **支援 XML 資料流**。 配接器用戶端可以將資料從或串流[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]利用**XMLReader**或是**XMLWriter**介面。  
  
- **支援 BizTalk Server 中的動態連接埠**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，則[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱 <<c0> [ 使用 Siebel 配接器設定動態連接埠](../../adapters-and-accelerators/adapter-siebel/configure-dynamic-ports-with-the-siebel-adapter.md)。  
  
- **訊息版本控制支援**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援訊息版本控制。 這可支援不同的訊息結構描述版本，後續的[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 訊息版本控制支援](../../adapters-and-accelerators/adapter-siebel/message-versioning-support2.md)。  
  
- **對效能計數器支援**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援配接器用戶端可以使用的 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱 < [Siebel 配接器的使用效能計數器](../../adapters-and-accelerators/adapter-siebel/use-performance-counters-with-the-siebel-adapter.md)。  
  
  > [!NOTE]
  >  這項功能不提供與舊版配接器的回溯相容性。  
  
- **對編碼的 XML 元素名稱**。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]當做 XML 中的項目名稱會顯示從企業應用程式的實體。 底線是可以包含在項目名稱的唯一特殊字元。 因此，底線用來編碼與特殊字元的項目名稱。 例如，`emp$name`編碼為`emp_x0024_name`。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Siebel eBusiness Applications 概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)