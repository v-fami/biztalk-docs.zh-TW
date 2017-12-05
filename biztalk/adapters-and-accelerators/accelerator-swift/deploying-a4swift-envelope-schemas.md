---
title: "部署 A4SWIFT 信封結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, envelope schemas
- A4SWIFT, deploying envelope schemas
- envelope schemas
- schemas, envelope schemas
ms.assetid: 6440608c-d30d-4d82-827a-8a4b2738db85
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8811f1dd056ca5a4ea4582d593af30e2ffc879f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-a4swift-envelope-schemas"></a>部署 A4SWIFT 信封結構描述
每當您設定 Message Repair 和 New Submission 時，您必須在結構描述專案中包含信封結構描述。 信封結構描述，例如 EnvelopeMT103.xsd，才能寫入 MRSR 網站。  
  
 **摘要**  
  
 加入信封結構描述您的專案，如下所示：  
  
-   在 Visual Studio 中，若要包含您的訊息結構描述的專案加入信封結構描述每個訊息結構描述。  
  
-   RuntimeSchemas.dll 參考加入至任何包含一個或多個信封結構描述的專案。  
  
    > [!NOTE]
    >  將參考加入至 RuntimeSchemas.dll 需[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]只在訊息修復和新送出至專案中加入信封結構描述專案。  
  
-   未剖析訊息信封結構描述 (EnvelopeUnparsedMessage.xsd) 加入專案。  
  
### <a name="to-add-a-swift-envelope-schema"></a>若要加入 SWIFT 信封結構描述  
  
1.  在 Visual Studio 的方案總管中開啟您的結構描述的專案。  
  
2.  以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
3.  在 [加入參考] 對話方塊中，按一下**瀏覽**標記。  
  
4.  在 [選取元件] 對話方塊中，開啟**查看**下拉式清單。 移至 ***\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\Assemblies**。 選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll**從組件，然後再按一下清單**新增**。  
  
5.  在**加入參考**對話方塊中，按一下 **確定**。  
  
6.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **加入現有項目**。  
  
7.  在 [新增現有的項目] 對話方塊中**查看**下拉式清單方塊中，移至**\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Categoryn\MTxxx**。 例如，選取信封結構描述， **EnvelopeMT103.xsd**，然後按一下 **新增**。  
  
     在 [新增現有的項目] 對話方塊中**查看**下拉式清單方塊中，移至。 選取信封結構描述，例如 EnvelopeMT103.xsd，然後按一下 [新增]。  
  
    > [!NOTE]
    >  A4SWIFT 加入信封結構描述，針對您的專案，在 [方案總管] 中所示。  
  
8.  在 方案總管 中，以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **加入現有項目**。  
  
9. 如果使用 Message Repair 和 New Submission 功能，在 [加入現有項目] 對話方塊中**查看**下拉式清單方塊中，移至  **\<*磁碟機*\>: \Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Unparsed 訊息 * *。 選取**EnvelopeUnparsedMessage.xsd**，然後按一下 **新增**。  
  
10. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。  
  
11. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。