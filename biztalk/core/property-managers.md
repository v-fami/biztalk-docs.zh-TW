---
title: 屬性管理員 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 823352a0-e397-464a-a163-1dbf8feea8d7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aff8fc39612ed79e6e9602ed39874d014bb4a11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269102"
---
# <a name="property-managers"></a><span data-ttu-id="39145-102">屬性管理員</span><span class="sxs-lookup"><span data-stu-id="39145-102">Property Managers</span></span>
<span data-ttu-id="39145-103">「屬性管理員」允許延伸模組將自訂屬性 (一般是 XSD 註解) 新增至結構描述的 XSD 表示法中的項目與屬性，也允許延伸 [屬性] 視窗，以包含與延伸模組相關聯的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="39145-103">Property Managers allow an extension to add custom properties (generally as XSD annotations) to elements and attributes in the XSD representation of the schema, as well as extending the Properties window to include the custom properties associated with the extension.</span></span>  
  
 <span data-ttu-id="39145-104">屬性管理員是一個物件，實作 **[ipropertymanager]** 介面，其參考透過呼叫**IExtension.GetPropertyManager**，並傳遞 **[Itreenode]** 物件做為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="39145-104">A Property Manager is an object that implements the **IPropertyManager** interface, a reference to which is obtained by calling **IExtension.GetPropertyManager**, and passing an **ITreeNode** object as the input parameter.</span></span> <span data-ttu-id="39145-105">通常延伸模組會提供一個 **[ipropertymanager]** 物件給每個 **[itreenode]** 物件。</span><span class="sxs-lookup"><span data-stu-id="39145-105">Typically the extension provides one **IPropertyManager** object for each **ITreeNode** object.</span></span> <span data-ttu-id="39145-106">屬性管理員會負責的自訂屬性集合，該 **[itreenode]** 物件。</span><span class="sxs-lookup"><span data-stu-id="39145-106">The Property Manager is responsible for the collection of custom properties for that **ITreeNode** object.</span></span>  
  
 <span data-ttu-id="39145-107">自訂屬性由**System.ComponentModel.PropertyDescriptor**物件，可以從所傳回的集合中取得**IPropertyManager.GetProperties**方法。</span><span class="sxs-lookup"><span data-stu-id="39145-107">A custom property is represented by a **System.ComponentModel.PropertyDescriptor** object, which can be obtained from the collection returned by the **IPropertyManager.GetProperties** method.</span></span>  
  
 <span data-ttu-id="39145-108">使用**PropertyDescriptor**物件，以表示延伸模組相關聯的自訂屬性有助於與 Microsoft 整合[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗。</span><span class="sxs-lookup"><span data-stu-id="39145-108">Using **PropertyDescriptor** objects to represent the custom properties associated with the extension facilitates integration with the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span> <span data-ttu-id="39145-109">當**PropertyDescriptor**物件使用，很容易 BizTalk 編輯器的整合已經整合到 [屬性] 視窗的標準節點屬性組中的擴充功能的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="39145-109">When **PropertyDescriptor** objects are used, it is easy for BizTalk Editor to integrate the custom properties of the extension into the set of standard node properties already being integrated into the Properties window.</span></span> <span data-ttu-id="39145-110">例如顯示名稱、 顯示值、 屬性控制項類型、 屬性描述和屬性類別目錄的自訂屬性資訊取自**PropertyDescriptor**物件。</span><span class="sxs-lookup"><span data-stu-id="39145-110">Custom property information such as the display name, the display value, the type of property control, the property description, and the property category is obtained from the **PropertyDescriptor** object.</span></span>  
  
 <span data-ttu-id="39145-111">自訂屬性儲存在結構描述的 XSD 表示法中，做為對應至結構描述樹狀結構中相關節點的項目中註解項目內的項目屬性。</span><span class="sxs-lookup"><span data-stu-id="39145-111">Custom properties are stored in the XSD representation of the schema as attributes of an element within the annotation element within the element corresponding to the relevant node in the schema tree.</span></span> <span data-ttu-id="39145-112">結構描述樹狀結構的每個自訂屬性都可以是通用項目的屬性，或者，每個自訂屬性都可擁有與其相關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="39145-112">Each custom property of a schema tree node can be an attribute of a common element, or alternatively, each can have its own associated element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39145-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39145-113">See Also</span></span>  
 [<span data-ttu-id="39145-114">延伸 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="39145-114">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)