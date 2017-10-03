---
title: "自訂配接器組態設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b231c3-3948-4db8-b4f0-d9c21c31b168
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e876892b3eef9e5dd47c51c64997d84a0f0dc98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="custom-adapter-configuration-designer"></a><span data-ttu-id="84b97-102">自訂配接器組態設計工具</span><span class="sxs-lookup"><span data-stu-id="84b97-102">Custom Adapter Configuration Designer</span></span>
<span data-ttu-id="84b97-103">您需要在 .NET 類別庫中建置自訂的設計工具。</span><span class="sxs-lookup"><span data-stu-id="84b97-103">You need to build the custom designers into a .NET class library.</span></span> <span data-ttu-id="84b97-104">您可以將這些設計工具整合到配接器的 DLL 中，或是另外建置 DLL。</span><span class="sxs-lookup"><span data-stu-id="84b97-104">You may incorporate them into the DLL for the adapter or build a separate DLL.</span></span> <span data-ttu-id="84b97-105">在建置設計工具組件之後，必須透過裝飾而加以參考，就如同描述或類別一樣。</span><span class="sxs-lookup"><span data-stu-id="84b97-105">After you build a designer assembly, you must reference it through decorations, just like a description or a category.</span></span> <span data-ttu-id="84b97-106">參考需包括組件的規格以及使用的完整格式類別名稱。</span><span class="sxs-lookup"><span data-stu-id="84b97-106">The reference includes a specification of the assembly and a fully qualified class name to use.</span></span>  
  
 <span data-ttu-id="84b97-107">這些裝飾支援兩種參考特定自訂設計工具： 在全域組件快取中的全域組件或磁碟上的外部組件。</span><span class="sxs-lookup"><span data-stu-id="84b97-107">These decorations support two ways of referencing the specific custom designer: as a global assembly in the global assembly cache or as an external assembly located on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84b97-108">有兩個可能的設計階段組件路徑： 您可以指定的型別編輯器和轉換器用於組態 XSD 中的 XSD 本身 （不支援相對路徑） 的絕對路徑，或者您可以在全域儲存型別編輯器和轉換器組件快取並不需要絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="84b97-108">There are two possible design-time assembly paths: You can specify the absolute path to the type editors and converters used in the configuration XSD in the XSD itself (relative path is not supported), or you can store the type editors and converters in the global assembly cache and not need an absolute path.</span></span>  
  
## <a name="global-assembly-cache-designer-use"></a><span data-ttu-id="84b97-109">全域組件快取設計工具的使用</span><span class="sxs-lookup"><span data-stu-id="84b97-109">Global Assembly Cache Designer Use</span></span>  
 <span data-ttu-id="84b97-110">全域組件快取會依照組件名稱、公開金鑰、版本和文化特性來儲存組件。</span><span class="sxs-lookup"><span data-stu-id="84b97-110">The global assembly cache stores assemblies by assembly name, public key, version, and culture.</span></span> <span data-ttu-id="84b97-111">因為這個原因，所以建議您：</span><span class="sxs-lookup"><span data-stu-id="84b97-111">Because of this, it is recommended that you:</span></span>  
  
1.  <span data-ttu-id="84b97-112">產生公開金鑰檔案，並將此檔案加入 AssemblyInfo.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="84b97-112">Generate a public key file and add this file to the AssemblyInfo.cs file.</span></span>  
  
2.  <span data-ttu-id="84b97-113">在 AssemblyInfo.cs 檔案中指定特定的版本。</span><span class="sxs-lookup"><span data-stu-id="84b97-113">Specify a specific version in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="84b97-114">您可以將組件拖曳到全域組件快取中，或使用 GACUTIL 將組件加入至全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="84b97-114">You can either drag the assembly into the global assembly cache or use GACUTIL to add it to the global assembly cache.</span></span>  
  
 <span data-ttu-id="84b97-115">若要使用此設計工具，請指定完整格式的類別名稱、逗號，以及全域組件快取的組件項目 (組件名稱、版本、文化特性和公開金鑰 Token)，以做為裝飾的值。</span><span class="sxs-lookup"><span data-stu-id="84b97-115">To use this designer, specify the fully qualified class name, a comma, and the global assembly cache assembly entry (assembly name, version, culture, and public key token) as the value of the decoration.</span></span> <span data-ttu-id="84b97-116">使用\<編輯器 > 裝飾**UITypeEditor**實作和\<轉換器 > 裝飾**TypeConverter**實作。</span><span class="sxs-lookup"><span data-stu-id="84b97-116">Use \<editor> decorations for **UITypeEditor** implementations and \<converter> decorations for **TypeConverter** implementations.</span></span>  
  
 <span data-ttu-id="84b97-117">下列程式碼範例將示範如何在 XSD 檔案中初始化自訂的設計工具。</span><span class="sxs-lookup"><span data-stu-id="84b97-117">The following code shows how to initialize the custom designers in an XSD file:</span></span>  
  
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
  
## <a name="external-assembly-installation-and-use"></a><span data-ttu-id="84b97-118">外部組件的安裝與使用</span><span class="sxs-lookup"><span data-stu-id="84b97-118">External Assembly Installation and Use</span></span>  
 <span data-ttu-id="84b97-119">如果是外部組件，裝飾會包含選擇性的屬性組件，這些組件可以為含有所要之設計工具的組件指定其完整路徑及名稱。</span><span class="sxs-lookup"><span data-stu-id="84b97-119">For external assemblies, the decoration contains an optional attribute assembly that specifies the full path and name of the assembly containing the desired designer.</span></span>  
  
 <span data-ttu-id="84b97-120">下列程式碼範例將示範如何在外部組件中初始化自訂的設計工具：</span><span class="sxs-lookup"><span data-stu-id="84b97-120">The following code shows how to initialize the custom designers contained in external assemblies:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84b97-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b97-121">See Also</span></span>  
 <span data-ttu-id="84b97-122">[配接器組態的自訂下拉式編輯器](../core/custom-drop-down-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="84b97-122">[Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md) </span></span>  
 <span data-ttu-id="84b97-123">[配接器組態的自訂強制回應對話方塊編輯器](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="84b97-123">[Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span></span>  
 <span data-ttu-id="84b97-124">[配接器組態的自訂類型轉換器](../core/custom-type-converter-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="84b97-124">[Custom Type Converter for Adapter Configuration](../core/custom-type-converter-for-adapter-configuration.md) </span></span>  
 [<span data-ttu-id="84b97-125">配接器的進階的組態元件</span><span class="sxs-lookup"><span data-stu-id="84b97-125">Advanced Configuration Components for Adapters</span></span>](../core/advanced-configuration-components-for-adapters.md)