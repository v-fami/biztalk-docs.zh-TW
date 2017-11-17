---
title: "進階組態元件的介面卡 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb31b996-6959-4b5a-9a9f-f48fd91a6180
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8307f54caffec269466dcd9398a9d911fdc83715
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-configuration-components-for-adapters"></a><span data-ttu-id="dc20f-102">配接器的進階的組態元件</span><span class="sxs-lookup"><span data-stu-id="dc20f-102">Advanced Configuration Components for Adapters</span></span>
<span data-ttu-id="dc20f-103">BizTalk 配接器架構支援自訂下拉式編輯器、自訂強制回應對話方塊編輯器，以及自訂類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="dc20f-103">The BizTalk Adapter Framework supports a custom drop-down editor, a custom modal dialog editor, and a custom type converter.</span></span> <span data-ttu-id="dc20f-104">這些自訂設計元件特別在接受輸入使用者名稱和密碼資訊時特別有幫助。</span><span class="sxs-lookup"><span data-stu-id="dc20f-104">These custom design components are especially useful when taking user name and password information as input.</span></span>  
  
 <span data-ttu-id="dc20f-105">您可以在組態結構描述中，叫用特定資料欄位 (項目或屬性) 的自訂編輯器或類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="dc20f-105">You can invoke a custom editor or type converter for a specific data field (element or attribute) in the configuration schema.</span></span> <span data-ttu-id="dc20f-106">Microsoft 中所述[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的說明，請在編輯器必須衍生自**System.Drawing.Design.UITypeEditor**和類型轉換器從**System.ComponentModel.TypeConverter**。</span><span class="sxs-lookup"><span data-stu-id="dc20f-106">As described in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help, the editor must be derived from **System.Drawing.Design.UITypeEditor** and the type converter from **System.ComponentModel.TypeConverter**.</span></span>  
  
 <span data-ttu-id="dc20f-107">編輯器至少會覆寫**GetEditStyle**方法，以指定編輯器的類型 (**強制回應** 對話方塊中，**下拉式**控制項，或**無**上述) 和**EditValue**方法，以變更編輯器的值。</span><span class="sxs-lookup"><span data-stu-id="dc20f-107">An editor minimally overrides the **GetEditStyle** method to specify the kind of editor (**Modal** dialog, **DropDown** control, or **None** of the above) and the **EditValue** method to change the value with the editor.</span></span>  
  
 <span data-ttu-id="dc20f-108">類型轉換器通常會覆寫**ConvertFrom**， **CanConvertFrom**， **ConvertTo**， **CanConvertTo**， **GetStandardValues**， **GetStandardValuesSupported**，和**GetStandardValuesExclusive**方法 .NET Framework 類別庫。</span><span class="sxs-lookup"><span data-stu-id="dc20f-108">A type converter typically overrides the **ConvertFrom**, **CanConvertFrom**, **ConvertTo**, **CanConvertTo**, **GetStandardValues**, **GetStandardValuesSupported**, and **GetStandardValuesExclusive**methods of the .NET Framework Class Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc20f-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="dc20f-109">In This Section</span></span>  
  
-   [<span data-ttu-id="dc20f-110">自訂配接器組態設計工具</span><span class="sxs-lookup"><span data-stu-id="dc20f-110">Custom Adapter Configuration Designer</span></span>](../core/custom-adapter-configuration-designer.md)  
  
-   [<span data-ttu-id="dc20f-111">配接器組態的自訂下拉式編輯器</span><span class="sxs-lookup"><span data-stu-id="dc20f-111">Custom Drop-Down Editor for Adapter Configuration</span></span>](../core/custom-drop-down-editor-for-adapter-configuration.md)  
  
-   [<span data-ttu-id="dc20f-112">配接器組態的自訂強制回應對話方塊編輯器</span><span class="sxs-lookup"><span data-stu-id="dc20f-112">Custom Modal Dialog Editor for Adapter Configuration</span></span>](../core/custom-modal-dialog-editor-for-adapter-configuration.md)  
  
-   [<span data-ttu-id="dc20f-113">配接器組態的自訂類型轉換器</span><span class="sxs-lookup"><span data-stu-id="dc20f-113">Custom Type Converter for Adapter Configuration</span></span>](../core/custom-type-converter-for-adapter-configuration.md)