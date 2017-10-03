---
title: "結構描述 Validation1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 599f1bbb-2af5-4278-8b0f-0e5a6517e8e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20224a77530139a97647d91b0b46f9384d6c2753
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-validation"></a><span data-ttu-id="95821-102">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="95821-102">Schema Validation</span></span>
<span data-ttu-id="95821-103">如果 BizTalk 編輯器 」 延伸模組提供**ISchemaValidator**物件時，架構會叫用**ISchemaValidator.ValidateSchema**當使用者叫用**驗證結構描述**命令，或在使用者建置包含結構描述的 BizTalk 專案的編譯期間。</span><span class="sxs-lookup"><span data-stu-id="95821-103">If a BizTalk Editor extension provides an **ISchemaValidator** object, the framework will invoke **ISchemaValidator.ValidateSchema** when the user invokes the **Validate Schema** command, or during compilation when the user builds the BizTalk project containing the schema.</span></span> <span data-ttu-id="95821-104">延伸模組通常會驗證的自訂屬性，並將錯誤訊息傳回做為陣列的**IValidationInfo**物件。</span><span class="sxs-lookup"><span data-stu-id="95821-104">The extension usually validates the custom properties, and can return error messages as an array of **IValidationInfo** objects.</span></span> <span data-ttu-id="95821-105">錯誤訊息會顯示在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] [工作清單] 視窗中，包含從 BizTalk 編輯器編譯器傳回的錯誤。</span><span class="sxs-lookup"><span data-stu-id="95821-105">The error messages are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Task List window, along with errors returned from BizTalk Editor compiler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95821-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95821-106">See Also</span></span>  
 [<span data-ttu-id="95821-107">延伸 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="95821-107">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)