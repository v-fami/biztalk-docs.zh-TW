---
title: 使用 IntelliSense 建立攔截器組態檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 349ea1bf-a5d1-4464-bf4b-d8746c622377
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7be3f79545db81a0127fc8d004d71c758069a55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287966"
---
# <a name="using-intellisense-to-create-an-interceptor-configuration-file"></a>使用 IntelliSense 建立攔截器組態檔
您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的 IntelliSense 和結構描述驗證，協助您建構結構描述上有效的攔截器組態檔。 BAM 管理公用程式會對照基本攔截器組態結構描述驗證您的攔截器組態檔，而且如果檔案無效，則不會部署結構描述。 如果檔案通過基本攔截器組態結構描述的驗證，則會在執行階段對照技術專屬結構描述 (如 [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] 結構描述或 [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 結構描述) 進行驗證，而如果發生錯誤，則不會進行攔截。 您可以在建構攔截器組態檔時，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的結構描述驗證來避開這些錯誤。  
  
> [!NOTE]
>  範例 BAM 攔截器組態 XSD 檔會隨 SDK 檔一併安裝。 檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs：  
>   
>  -   CommonInterceptorConfiguration.xsd  
> -   WcfInterceptorConfiguration.xsd  
> -   WorkflowInterceptorConfiguration.xsd  
  
### <a name="to-obtain-a-copy-of-the-interceptor-schemas"></a>取得攔截器結構描述的副本  
  
1.  開啟「記事本」或其他文字編輯器。  
  
2.  瀏覽至[攔截器組態結構描述](../core/interceptor-configuration-schema.md)主題。  
  
3.  內容貼到新的文件中，開啟文字編輯器，然後將檔案儲存為文字檔，使用名稱**CommonInterceptorConfiguration.xsd** （或您自己選擇的其中一個） 至硬碟。  
  
4.  重複這些步驟[!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)]結構描述和[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]使用檔案名稱的結構描述主題**WorkflowInterceptorConfiguration.xsd**和**WcfInterceptorConfiguration.xsd**或名稱您自己的選擇。  
  
### <a name="to-use-intellisense-with-your-interceptor-configuration-file"></a>搭配攔截器組態檔使用 IntelliSense  
  
1.  開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2.  按一下**檔案**，按一下 **新增**，然後按一下 **檔案**。  
  
3.  在**新檔案**對話方塊中，選取**XML 檔案**，然後按一下 **開啟**。  
  
4.  檢視 [屬性] 窗格，以滑鼠右鍵按一下 [編輯] 窗格中，然後按一下**屬性**。  
  
5.  在 [屬性] 窗格中，按一下**結構描述**，然後按一下省略符號 (**...**).  
  
6.  在**XML 結構描述**對話方塊中，按一下 **新增**然後瀏覽至該結構描述，然後選取位置**CommonInterceptorConfiguration.xsd**和**WcfInterceptorConfiguration.xsd**如果您正在使用[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]攔截器組態檔，或**WorkflowInterceptorConfiguration.xsd**如果您正在使用[!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)]攔截器組態檔。  
  
    > [!NOTE]
    >  如果您使用不同的名稱儲存檔案，則選取這些檔案。  
  
7.  現在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會在攔截器組態檔開啟時進行驗證，並且提供 IntelliSense 協助您建立和修改檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Workflow Foundation 結構描述](../core/windows-workflow-foundation-schema.md)   
 [Windows Communication Foundation 結構描述](../core/windows-communication-foundation-schema.md)