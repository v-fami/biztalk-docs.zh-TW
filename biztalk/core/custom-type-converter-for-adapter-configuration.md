---
title: "配接器組態的自訂類型轉換器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60e94dde-d29d-43ff-84b0-b2ba86851151
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6285cd61fd0738fb97c6192cd52b812d96ede7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="custom-type-converter-for-adapter-configuration"></a><span data-ttu-id="3e2a0-102">配接器組態的自訂類型轉換器</span><span class="sxs-lookup"><span data-stu-id="3e2a0-102">Custom Type Converter for Adapter Configuration</span></span>
<span data-ttu-id="3e2a0-103">如同自訂編輯器，自訂類型轉換器會覆寫**System.ComponentModel.TypeConverter**類別的其中一個子系。</span><span class="sxs-lookup"><span data-stu-id="3e2a0-103">Like the custom editor, the custom type converter overrides the **System.ComponentModel.TypeConverter** class of one of its children.</span></span> <span data-ttu-id="3e2a0-104">在這裡，轉換器會將格式新增至要保存的值，但不會出現在屬性頁上。</span><span class="sxs-lookup"><span data-stu-id="3e2a0-104">Here, the converter adds formatting to the value to be persisted but does not appear on the property page.</span></span> <span data-ttu-id="3e2a0-105">**ConvertFrom**方法會將方括號括住的字串值和**ConvertTo**方法會將它們移除。</span><span class="sxs-lookup"><span data-stu-id="3e2a0-105">The **ConvertFrom** method adds square brackets around the string value and the **ConvertTo** method removes them.</span></span>  
  
 <span data-ttu-id="3e2a0-106">下列程式碼為自訂類型轉換器的類別定義：</span><span class="sxs-lookup"><span data-stu-id="3e2a0-106">The following code is the class definition for the custom type converter:</span></span>  
  
```  
using System;  
using System.ComponentModel;  
  
namespace AdapterManagement.ComponentModel {  
  
   public class DesignerTypeConverter : StringConverter {  
  
      public override bool CanConvertTo(ITypeDescriptorContext context, Type destinationType) {  
         return (typeof(String) == destinationType) || base.CanConvertTo (context, destinationType);  
      }  
  
      public override object ConvertTo(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object value, Type destinationType) {  
         if (typeof(String) == destinationType && value is String) {  
            return ((String)value).TrimStart('[').TrimEnd(']');  
         }  
         return base.ConvertTo (context, culture, value, destinationType);  
      }  
  
      public override bool CanConvertFrom(ITypeDescriptorContext context, Type sourceType) {  
         return (typeof(String) == sourceType) || base.CanConvertFrom (context, sourceType);  
      }  
  
      public override object ConvertFrom(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object value) {  
         if (value is String) {  
            return "["+(String)value+"]";  
         }  
         return base.ConvertFrom (context, culture, value);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e2a0-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e2a0-107">See Also</span></span>  
 <span data-ttu-id="3e2a0-108">[自訂配接器組態設計工具](../core/custom-adapter-configuration-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3e2a0-108">[Custom Adapter Configuration Designer](../core/custom-adapter-configuration-designer.md) </span></span>  
 <span data-ttu-id="3e2a0-109">[配接器組態的自訂下拉式編輯器](../core/custom-drop-down-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3e2a0-109">[Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md) </span></span>  
 <span data-ttu-id="3e2a0-110">[配接器組態的自訂強制回應對話方塊編輯器](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3e2a0-110">[Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span></span>  
 [<span data-ttu-id="3e2a0-111">配接器的進階的組態元件</span><span class="sxs-lookup"><span data-stu-id="3e2a0-111">Advanced Configuration Components for Adapters</span></span>](../core/advanced-configuration-components-for-adapters.md)