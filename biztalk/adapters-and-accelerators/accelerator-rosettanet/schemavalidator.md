---
title: SchemaValidator |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, SchemaValidator utility
- validating, SchemaValidator utility
- SchemaValidator utility
- schemas, SchemaValidator utility
ms.assetid: 3bd61a03-d81e-4fd1-802c-f801000002d7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0291e5b901b6da3c19208f23846912ac16658ab6
ms.sourcegitcommit: 436ebffd959a9c4bdaafd4da9a5843c59a018eb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "34855465"
---
# <a name="schemavalidator"></a>SchemaValidator
您可以使用 SchemaValidator 公用程式，疑難排解訊息執行個體的問題。 如果您收到驗證失敗的訊息，可以執行 SchemaValidator 公用程式找出失敗的原因。  
  
 如果要使用含有結構描述 .dll 檔的組件，並且您沒有結構描述 .xsd 檔，請使用這個公用程式。 SchemaValidator 公用程式讓您可以使用結構描述 .dll 檔進行驗證。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\SchemaValidator  
  
## <a name="building-and-running-schemavalidator"></a>建置和執行 SchemaValidator  
  
#### <a name="to-build-the-schemavalidator-utility"></a>建置 SchemaValidator 公用程式  
  
1.  開啟命令提示字元。  
  
2.  移至\<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\SchemaValidator。  
  
3.  在命令提示字元中，輸入**sn-k SchemaValidator.snk**，然後按 ENTER 鍵。  
  
4.  啟動**Microsoft Visual Studio 2012**。  
  
5.  在**檔案**功能表上，指向**開啟**，然後按一下 **開啟的方案**。  
  
6.  移至\<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\SchemaValidator，選取**SchemaValidator.sln**，然後按一下 **開啟**。  
  
7.  在 方案總管 中，以滑鼠右鍵按一下**SchemaValidator**，然後按一下 **屬性**。  
  
8.  在**MessageInspector 屬性**頁面上，按一下**簽署**索引標籤，然後再按一下**簽署組件**核取方塊。 選取**SchemaValidator.snk**中**選擇強式名稱金鑰檔**。  
  
9. 按一下**SchemaValidator.cs**。  
  
10. 在下列 `Main` 的現有程式碼行中，輸入適當的訊息執行個體路徑：  
  
    ```  
    const string xmlInstancePath = @"..\..\Sample3A4.xml";  
    ```  
  
11. 使用 RNPIP 組件的參考取代下列 `Main` 中的現有程式碼行，然後選取適當的結構描述：  
  
    ```  
    _3A4_MS_V02_02_PurchaseOrderRequest BTSSchema = new _3A4_MS_V02_02_PurchaseOrderRequest();  
    ```  
  
12. 以滑鼠右鍵按一下**SchemaValidator**，然後按一下 **建置**。  
  
13. 修改訊息執行個體至您想要藉由移除測試\< \!DOCTYPE...\>指定從 XML 執行個體的標頭的 DTD 檔案的標記。  
  
14. 在訊息執行個體的根節點中，加入將要進行驗證之結構描述的 XML 命名空間。  
  
    > [!NOTE]
    >  如需可以由 SchemaValidator 公用程式進行驗證的結構描述的範例，請參閱中的 Sample3A4.xml \<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\SchemaValidator。  
  
15. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下  **SchemaValidator.cs**，然後按下 CTRL 和 F5 執行公用程式。  
  
## <a name="remarks"></a>備註  
 由於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含 SchemaValidator 程式碼，因此您可以在公用程式中加入邏輯。 例如，您可以讓公用程式成為命令列公用程式。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
