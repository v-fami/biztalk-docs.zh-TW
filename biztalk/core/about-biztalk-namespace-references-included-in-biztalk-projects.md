---
title: 關於在 BizTalk 專案中包含的 BizTalk 命名空間參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.Xml namespace
- Microsoft.BizTalk.GlobalPropertySchemas namespace
- namespaces, System.Xml namespace
- System namespace
- namespaces, System namespace
- namespaces, Microsoft.BizTalk.GlobalPropertySchemas namespace
- Microsoft.BizTalk.DefaultPipelines namespace
- projects, namespaces
- namespaces, warnings
- namespaces, Microsoft.BIzTalk.DefaultPipelines namespace
- namespaces
ms.assetid: cb642eac-7307-44f8-bbba-3ae364e11ea2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 820e15eb3524713dfd7d3f86311ca262fde191d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225174"
---
# <a name="about-biztalk-namespace-references-included-in-biztalk-projects"></a>關於在 BizTalk 專案中包含的 BizTalk 命名空間參考
當您新增新的 BizTalk 專案時，預設會包含下列命名空間：  
  
-   **Microsoft.BizTalk.DefaultPipelines**  
  
-   **Microsoft.BizTalk.GlobalPropertySchemas**  
  
-   **系統**  
  
-   **System.Xml**  
  
 您也可以將新的參考和 Web 參考新增到您的專案。 如需有關加入參考使用**專案**功能表上，請參閱[使用 Visual Studio](../core/using-visual-studio.md)。 如需新增 Web 參考資訊，請參閱[加入 Web 參考](../core/adding-web-references.md)。  
  
> [!CAUTION]
>  請勿移除預設參考。 如果您移除預設參考，您可能會在專案中參考 BizTalk 項目時遇到問題。 您可以在方案總管中還原預設參考。  
  
> [!CAUTION]
>  如果您的 BizTalk 專案參考另一個組件，而該組件已經更新，那麼在您的 BizTalk 專案中不會自動選擇更新或變更。 您應該移除方案總管中已過期的參考，然後再次新增參考 (重新參考組件)。 或者，您可以關閉您的方案然後重新開啟。 不論使用哪種方式，您的專案都可以使用參考組件的最新更新。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Microsoft.BizTalk.DefaultPipelines 參考](../core/microsoft-biztalk-defaultpipelines-reference.md)  
  
-   [Microsoft.BizTalk.GlobalPropertySchemas 參考](../core/microsoft-biztalk-globalpropertyschemas-reference.md)  
  
-   [System 參考](../core/system-reference.md)  
  
-   [System.Xml 參考](../core/system-xml-reference.md)