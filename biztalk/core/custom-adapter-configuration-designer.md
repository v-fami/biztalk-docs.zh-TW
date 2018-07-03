---
title: 自訂配接器組態設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9b231c3-3948-4db8-b4f0-d9c21c31b168
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60754ea86e3c77534a15d00ff18b21705198d648
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014439"
---
# <a name="custom-adapter-configuration-designer"></a>自訂配接器組態設計工具
您需要在 .NET 類別庫中建置自訂的設計工具。 您可以將這些設計工具整合到配接器的 DLL 中，或是另外建置 DLL。 在建置設計工具組件之後，必須透過裝飾而加以參考，就如同描述或類別一樣。 參考需包括組件的規格以及使用的完整格式類別名稱。  
  
 這些裝飾支援兩種參考特定的自訂設計工具： 在全域組件快取中的全域組件或外部組件的磁碟上。  
  
> [!NOTE]
>  有兩種可能的設計階段組件路徑： 您可以指定的型別編輯器和轉換器用於組態 XSD 中的 XSD 本身 （不支援相對路徑） 的絕對路徑，或者您可以在全域儲存型別編輯器和轉換器組件快取並不需要絕對路徑。  
  
## <a name="global-assembly-cache-designer-use"></a>全域組件快取設計工具的使用  
 全域組件快取會依照組件名稱、公開金鑰、版本和文化特性來儲存組件。 因為這個原因，所以建議您：  
  
1. 產生公開金鑰檔案，並將此檔案加入 AssemblyInfo.cs 檔案。  
  
2. 在 AssemblyInfo.cs 檔案中指定特定的版本。  
  
   您可以將組件拖曳到全域組件快取中，或使用 GACUTIL 將組件加入至全域組件快取中。  
  
   若要使用此設計工具，請指定完整格式的類別名稱、逗號，以及全域組件快取的組件項目 (組件名稱、版本、文化特性和公開金鑰 Token)，以做為裝飾的值。 使用\<編輯器\>裝飾**UITypeEditor**實作並\<轉換器\>裝飾**TypeConverter**實作.  
  
   下列程式碼範例將示範如何在 XSD 檔案中初始化自訂的設計工具。  
  
```  
<xs:element name="Global" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>GAC Designer Component</baf:category>  
            <baf:editor>AdapterManagement.ComponentModel. PasswordUITypeEditor, AdapterManagement, Version=1.0.1.0, Culture=neutral, PublicKeyToken=f0db50abb0615c18</baf:editor>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
      </xs:sequence>  
```  
  
## <a name="external-assembly-installation-and-use"></a>外部組件的安裝與使用  
 如果是外部組件，裝飾會包含選擇性的屬性組件，這些組件可以為含有所要之設計工具的組件指定其完整路徑及名稱。  
  
 下列程式碼範例將示範如何在外部組件中初始化自訂的設計工具：  
  
```  
<xs:element name="External" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>External Designer Component</baf:category>  
            <baf:converter assembly="C:\source\private\Adapter\Framework\Designer\bin\Debug\Designer.External.dll">Designer.External.DesignerTypeConverter</baf:converter>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
```  
  
## <a name="see-also"></a>另請參閱  
 [配接器組態的自訂下拉式編輯器](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [配接器組態的自訂強制回應對話方塊編輯器](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [配接器組態的自訂類型轉換器](../core/custom-type-converter-for-adapter-configuration.md)   
 [配接器的進階設定元件](../core/advanced-configuration-components-for-adapters.md)