---
title: 管理結構描述 |Microsoft 文件
description: 使用在 BizTalk Server 中，包括顯示和隱藏屬性結構描述使用 BizTalk 管理 檢視的 XSD，啟用追蹤
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5632e79-b182-41c9-9138-eb88b44e3172
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0d7fe3eee97cf81c668ffe90fd9c0897af23cc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262598"
---
# <a name="manage-schemas"></a>管理結構描述

## <a name="overiew"></a>概觀
本節提供使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台管理結構描述的指示。 結構描述可供管線及協調流程用來呈現所要處理的訊息。  
  
 結構描述是在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立，並編譯成 BizTalk 組件。 您不能將結構描述個別新增到應用程式中；結構描述會在下列情況中新增至應用程式：  
  
-   當您新增 BizTalk 組件包含應用程式，結構描述中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
-   當您匯入.msi 檔案包含結構描述，其中包含 BizTalk 組件中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
-   當開發人員應用程式組件部署到包含從結構描述[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述，[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
 如需結構描述的背景資訊，請參閱[結構描述](../core/schemas.md)。 如需開發結構描述的詳細資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟 
  
-   [顯示和隱藏屬性結構描述](../core/how-to-show-and-hide-property-schemas.md)  
  
-   [檢視結構描述定義 (XSD) 結構描述](../core/how-to-view-the-schema-definition-xsd-of-a-schema.md)  
  
-   [設定追蹤之結構描述](../core/how-to-configure-tracking-for-a-schema.md)  
  
-   [從應用程式移除結構描述](../core/how-to-remove-a-schema-from-an-application.md)