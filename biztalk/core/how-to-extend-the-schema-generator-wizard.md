---
title: 如何擴充結構描述產生器精靈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- utilities, Schema Generator Wizard
- Schema Generator Wizard
ms.assetid: ea4b5532-f904-4da0-9612-e092e7e4edc1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6fb901186dddf69a94fca4467b543f047c27719
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013807"
---
# <a name="how-to-extend-the-schema-generator-wizard"></a><span data-ttu-id="9dea8-102">如何擴充結構描述產生器精靈</span><span class="sxs-lookup"><span data-stu-id="9dea8-102">How to Extend the Schema Generator Wizard</span></span>
<span data-ttu-id="9dea8-103">如何擴充現有的結構描述產生器精靈以及如何建立新的精靈來產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="9dea8-103">How to extend the existing Schema Generator Wizard and how to create a new wizard for schema generation.</span></span>  
  
## <a name="extend-the-existing-schema-wizard"></a><span data-ttu-id="9dea8-104">擴充現有的結構描述精靈</span><span class="sxs-lookup"><span data-stu-id="9dea8-104">Extend the existing schema wizard</span></span>  
  
1. <span data-ttu-id="9dea8-105">實作 ISchemaGenerator 介面以建立新的結構描述產生器模組，您可以將整合到現有的結構描述產生器精靈。</span><span class="sxs-lookup"><span data-stu-id="9dea8-105">Implement the ISchemaGenerator interface to create a new schema generator module that you can integrate into the existing Schema Generator Wizard.</span></span>  
  
   ```  
   public interface ISchemaGenerator  
   {  
   //Method to extract a schema from a document.  
   void GenerateSchema(string inputDocument,string outputDocumentPath);  
  
   //Method to extract the errors.  
   [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] Errors();  
  
   //Method to extract the warnings.  
   [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] Warnings();  
  
   //Method to extract the referenced schemas.  
   [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] ReferencedSchemas();  
   }  
   ```  
  
2. <span data-ttu-id="9dea8-106">將產生的組件放入下列 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9dea8-106">Drop the resulting assembly in the following Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder:</span></span>  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="9dea8-107">\Developer Tools\Schema 編輯器延伸模組</span><span class="sxs-lookup"><span data-stu-id="9dea8-107">\Developer Tools\Schema Editor Extensions</span></span>  
  
    <span data-ttu-id="9dea8-108">結構描述產生器精靈下次執行時，就會自動採用新的結構描述產生器模組：</span><span class="sxs-lookup"><span data-stu-id="9dea8-108">The next time you run the Schema Generator Wizard, it will automatically pick up your new schema generator module.</span></span>  
  
   <span data-ttu-id="9dea8-109">使用下列程序來建立新的結構描述精靈。</span><span class="sxs-lookup"><span data-stu-id="9dea8-109">Use the following procedure to create a new schema wizard.</span></span>  
  
   <span data-ttu-id="9dea8-110">**SDK 中的位置**</span><span class="sxs-lookup"><span data-stu-id="9dea8-110">**Location in SDK**</span></span>  
  
   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="9dea8-111">\SDK\Utilities\Schema generator</span><span class="sxs-lookup"><span data-stu-id="9dea8-111">\SDK\Utilities\Schema Generator</span></span>  
  
### <a name="create-a-new-schema-wizard"></a><span data-ttu-id="9dea8-112">建立新的結構描述精靈</span><span class="sxs-lookup"><span data-stu-id="9dea8-112">Create a new schema wizard</span></span>  
  
1. <span data-ttu-id="9dea8-113">執行 InstallDTD.vbs 以將 Microsoft.BizTalk.DTDToXSDGenerator.dll 安裝至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema 編輯器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9dea8-113">Run InstallDTD.vbs to install Microsoft.BizTalk.DTDToXSDGenerator.dll to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Editor Extensions.</span></span> <span data-ttu-id="9dea8-114">DTDToXSDGenerator.dll 會公開用來將 DTD 檔案轉換為 XSD 的類別。</span><span class="sxs-lookup"><span data-stu-id="9dea8-114">DTDToXSDGenerator.dll exposes classes you can use to convert DTD files to XSD.</span></span>  
  
2. <span data-ttu-id="9dea8-115">執行 InstallWFX.vbs 以將 Microsoft.BizTalk.WFXToXSDGenerator.dll 安裝至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema 編輯器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9dea8-115">Run InstallWFX.vbs to install Microsoft.BizTalk.WFXToXSDGenerator.dll to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Editor Extensions.</span></span> <span data-ttu-id="9dea8-116">WFXToXSDGenerator.dll 會公開用來將 WFX 檔案轉換為 XSD 的類別。</span><span class="sxs-lookup"><span data-stu-id="9dea8-116">WFXToXSDGenerator.dll exposes classes you can use to convert WFX files to XSD.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dea8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dea8-117">See Also</span></span>  
 [<span data-ttu-id="9dea8-118">SDK 中的公用程式</span><span class="sxs-lookup"><span data-stu-id="9dea8-118">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)