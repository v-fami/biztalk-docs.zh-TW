---
title: 連接至 Siebel 系統在 Visual Studio 中使用使用配接器服務增益集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2baaa361-1b14-4d00-bcef-f68bc3fa7139
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9916dc1328412428e4f21858905a005e35d9d1d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013815"
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-consume-adapter-service-add-in"></a>連接至 Siebel 系統在 Visual Studio 中使用使用配接器服務增益集
[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]您安裝時安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]載入電腦上安裝的所有 WCF 自訂繫結。 使用 WCF 型 Siebel 系統連接[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在 BizTalk 專案中，您必須使用**siebelBinding**。  

## <a name="connecting-to-a-siebel-system-using-consume-adapter-service-add-in"></a>連接至 Siebel 系統，請使用使用配接器服務增益集  
 執行下列步驟來連接到 Siebel 系統使用[!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)]。  

#### <a name="to-connect-to-a-siebel-system"></a>若要連接至 Siebel 系統  

1. 若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：  

   1. 建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

   2. 以滑鼠右鍵按一下方案總管 中的專案，指向**新增**，然後按一下**新增產生的項目**。  

   3. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


      |    使用    |             以進行此動作             |
      |----------------|------------------------------------|
      | **類別** | 按一下 **取用配接器服務**。 |
      | **範本**  | 按一下 **取用配接器服務**。 |


   4. 按一下 **[加入]**。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]隨即開啟。  

2. 從**選取的繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**。  

3. 中**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.  

4. 指定的使用者名稱和密碼來連接至 Siebel 系統。  

5. 按一下  **URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  

   > [!NOTE]
   >  如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

6. 按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  

7. 按一下 [確定] 。  

8. 按一下 **[連接]**。 一旦建立連線之後，連線狀態會顯示為**Connected**。  

    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。  

    ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")  

    [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點，其中包含可對 Siebel 系統的各種作業。 例如，**商務物件**節點包含所有的商務物件和可叫用 Siebel 系統的商務元件。 同樣地，**商務服務**節點包含在您連接至 Siebel 系統的所有商務服務。 如需有關這些節點的詳細資訊，請參閱 <<c0> [ 中繼資料節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。