---
title: "啟用配接器架構組態延伸模組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 851f4a20-502d-45f8-9647-13bec33fa460
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346bbc3d4d136ad7116a68b3c57a47566f258a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-adapter-framework-configuration-extensions"></a><span data-ttu-id="48e4a-102">啟用配接器架構組態延伸模組</span><span class="sxs-lookup"><span data-stu-id="48e4a-102">Enabling Adapter Framework Configuration Extensions</span></span>
<span data-ttu-id="48e4a-103">「BizTalk 配接器架構」提供數個可改善使用者體驗的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="48e4a-103">The BizTalk Adapter Framework provides several extensions to improve the user experience.</span></span> <span data-ttu-id="48e4a-104">若要使用這些擴充功能，匯入架構的結構描述 BiztalkAdapterFramework.xsd。</span><span class="sxs-lookup"><span data-stu-id="48e4a-104">To use these extensions, import the framework's schema, BiztalkAdapterFramework.xsd.</span></span> <span data-ttu-id="48e4a-105">匯入結構描述可讓您可以存取裝飾和特定的類型，並將它們用於配接器的組態結構描述，如下所述。</span><span class="sxs-lookup"><span data-stu-id="48e4a-105">Importing the schema enables you to access decorations and specialized types and to use them in the adapter's configuration schema, as described below.</span></span> <span data-ttu-id="48e4a-106">下列程式碼顯示如何匯入此結構描述：</span><span class="sxs-lookup"><span data-stu-id="48e4a-106">The following code shows how to import the schema:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?><xs:schema   targetNamespace="http://tempuri.org/XMLSchema.xsd"   
         elementFormDefault="qualified" xmlns="http://tempuri.org/XMLSchema.xsd"   
         xmlns:baf="BiztalkAdapterFramework.xsd"   
         xmlns:xs="http://www.w3.org/2001/XMLSchema"   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:import namespace="BiztalkAdapterFramework.xsd" />  
. . .  
</xs:schema>  
```  
  
## <a name="importing-the-biztalk-adapter-framework-extensions-schema-xsd"></a><span data-ttu-id="48e4a-107">匯入 BizTalk 配接器架構延伸模組結構描述 XSD</span><span class="sxs-lookup"><span data-stu-id="48e4a-107">Importing the BizTalk Adapter Framework Extensions Schema XSD</span></span>  
 <span data-ttu-id="48e4a-108">藉由匯入配接器架構延伸模組結構描述 XSD，您可以使用裝飾例如\<baf:FileName > 做為項目的類型，其中顯示檔案名稱的快顯時編輯項目。</span><span class="sxs-lookup"><span data-stu-id="48e4a-108">By importing the Adapter Framework extensions schema XSD, you can use decorations such as \<baf:FileName> as an element's type, which shows the file name pop-up when editing the element.</span></span>  
  
 <span data-ttu-id="48e4a-109">其他裝飾會控制屬性在介面中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="48e4a-109">Additional decorations control the display of the property in the interface.</span></span> <span data-ttu-id="48e4a-110">\<Baf: description > 裝飾，例如，加入說明文字的項目。</span><span class="sxs-lookup"><span data-stu-id="48e4a-110">The \<baf:description> decoration, for example, adds help text to the element.</span></span> <span data-ttu-id="48e4a-111">\<Baf: description > 裝飾底部的屬性頁上顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="48e4a-111">The \<baf:description> decoration displays the text at the bottom of the property page.</span></span> <span data-ttu-id="48e4a-112">\<Browsable>： 可瀏覽 > 裝飾會隱藏在介面中的項目。</span><span class="sxs-lookup"><span data-stu-id="48e4a-112">The \<baf:browsable> decoration hides an element from the interface.</span></span> <span data-ttu-id="48e4a-113">下列程式碼顯示如何在組態結構描述中使用這些項目：</span><span class="sxs-lookup"><span data-stu-id="48e4a-113">The following code shows how you can use these elements within a configuration schema:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?><xs:schema   targetNamespace="http://tempuri.org/XMLSchema.xsd"   
         elementFormDefault="qualified" xmlns="http://tempuri.org/XMLSchema.xsd"   
         xmlns:baf="BiztalkAdapterFramework.xsd"   
         xmlns:xs="http://www.w3.org/2001/XMLSchema"   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:import namespace="BiztalkAdapterFramework.xsd" />  
   <xs:element name="Send">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="directory" type="xs:string" />  
               <xs:annotation>  
                  <xs:appinfo>  
                     <baf:designer>  
                        <baf:description>Enter the directory that will receive sent files..  
                        </baf:description>  
                     </baf:designer>  
                  </xs:appinfo>  
               </xs:annotation>  
            </xs:element>  
            <xs:element name="fileName" type="" />  
            <xs:element name="sendBatchSize" type="xs:int" />  
            <xs:element name="fileCopyMode" type="CopyMode" />  
            <xs:element name="uri" type="xs:string" >  
               <xs:annotation>  
                  <xs:appinfo>  
                     <baf:designer>  
                        <baf:browsable show="false" />  
                     </baf:designer>  
                  </xs:appinfo>  
               </xs:annotation>  
            </xs:element>  
         </xs:sequence>  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="CopyMode">  
      <xs:restriction base="xs:string">  
         <xs:enumeration value="Append">  
            <xs:annotation>  
               <xs:documentation>= 0</xs:documentation>  
            </xs:annotation>  
         <xs:enumeration value="Create">  
            <xs:annotation>  
               <xs:documentation>= 1</xs:documentation>  
            </xs:annotation>  
         <xs:enumeration value="CreateNew">  
            <xs:annotation>  
               <xs:documentation>= 2</xs:documentation>  
            </xs:annotation>  
         </xs:enumeration>  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48e4a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48e4a-114">See Also</span></span>  
 [<span data-ttu-id="48e4a-115">配接器架構組態結構描述延伸模組</span><span class="sxs-lookup"><span data-stu-id="48e4a-115">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)