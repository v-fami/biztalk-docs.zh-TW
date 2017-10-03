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
# <a name="custom-type-converter-for-adapter-configuration"></a>配接器組態的自訂類型轉換器
如同自訂編輯器，自訂類型轉換器會覆寫**System.ComponentModel.TypeConverter**類別的其中一個子系。 在這裡，轉換器會將格式新增至要保存的值，但不會出現在屬性頁上。 **ConvertFrom**方法會將方括號括住的字串值和**ConvertTo**方法會將它們移除。  
  
 下列程式碼為自訂類型轉換器的類別定義：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [自訂配接器組態設計工具](../core/custom-adapter-configuration-designer.md)   
 [配接器組態的自訂下拉式編輯器](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [配接器組態的自訂強制回應對話方塊編輯器](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [配接器的進階的組態元件](../core/advanced-configuration-components-for-adapters.md)