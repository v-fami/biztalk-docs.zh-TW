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
# <a name="how-to-extend-the-schema-generator-wizard"></a>如何擴充結構描述產生器精靈
如何擴充現有的結構描述產生器精靈以及如何建立新的精靈來產生結構描述。  
  
## <a name="extend-the-existing-schema-wizard"></a>擴充現有的結構描述精靈  
  
1. 實作 ISchemaGenerator 介面以建立新的結構描述產生器模組，您可以將整合到現有的結構描述產生器精靈。  
  
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
  
2. 將產生的組件放入下列 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾中：  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema 編輯器延伸模組  
  
    結構描述產生器精靈下次執行時，就會自動採用新的結構描述產生器模組：  
  
   使用下列程序來建立新的結構描述精靈。  
  
   **SDK 中的位置**  
  
   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\SDK\Utilities\Schema generator  
  
### <a name="create-a-new-schema-wizard"></a>建立新的結構描述精靈  
  
1. 執行 InstallDTD.vbs 以將 Microsoft.BizTalk.DTDToXSDGenerator.dll 安裝至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema 編輯器延伸模組。 DTDToXSDGenerator.dll 會公開用來將 DTD 檔案轉換為 XSD 的類別。  
  
2. 執行 InstallWFX.vbs 以將 Microsoft.BizTalk.WFXToXSDGenerator.dll 安裝至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema 編輯器延伸模組。 WFXToXSDGenerator.dll 會公開用來將 WFX 檔案轉換為 XSD 的類別。  
  
## <a name="see-also"></a>另請參閱  
 [SDK 中的公用程式](../core/utilities-in-the-sdk.md)