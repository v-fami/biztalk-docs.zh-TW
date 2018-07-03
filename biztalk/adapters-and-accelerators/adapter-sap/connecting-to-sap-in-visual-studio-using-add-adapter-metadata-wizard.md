---
title: 在 Visual Studio 中使用連接至 SAP 新增配接器中繼資料精靈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a442837b-e7d8-4edb-9c5e-5603d4c58fe5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74b2070ecf59e76ec587fae3e2bc3be20b5b7976
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989255"
---
# <a name="connecting-to-sap-in-visual-studio-using-add-adapter-metadata-wizard"></a>在 Visual Studio 中使用連接至 SAP 新增配接器中繼資料精靈
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也會公開為 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述您想要在使用配接器的 SAP 系統上執行的作業。  

## <a name="connecting-to-an-sap-system-using-add-adapter-metadata-wizard"></a>連接到 SAP 系統使用新增配接器中繼資料精靈  
 執行下列步驟來連接到 SAP 系統使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-connect-to-an-sap-system"></a>若要連接到 SAP 系統  

1. 若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：  

   1. 建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

   2. 以滑鼠右鍵按一下方案總管 中的專案名稱，指向**新增**，然後按一下**新增產生的項目**。  

   3. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


      |    使用    |           以進行此動作            |
      |----------------|---------------------------------|
      | **類別** |     按一下 **新增介面卡**。      |
      | **範本**  | 按一下 **新增配接器中繼資料**。 |


   4. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

   5. 在 [新增配接器精靈] 中，選取**WCF-SAP**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  

      > [!IMPORTANT]
      >  如果您已經在 BizTalk 中設定的 WCF SAP 連接埠，請選取 從連接埠**連接埠**清單。  

   6. 按 [下一步] 。  

2. 從**選取的繫結**下拉式清單中，選取**sapBinding**然後按一下**設定**。  

3. 中**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連線到 SAP 系統。  

   > [!IMPORTANT]
   >  如果您使用 SAP 安全網路連線 (SNC) 程式庫來連接到 SAP 系統，請勿指定使用者名稱和密碼。  

4. 按一下  **URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  

   > [!IMPORTANT]
   >  如果您使用 SAP SNC 程式庫來連接到 SAP 系統，設定**UseSnc**連接屬性設 **，則為 True**。  

   > [!NOTE]
   >  如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

5. 按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 例如，如果您想要為目標的 ReceiveIdoc 作業您必須設定**ReceiveIdocFormat**屬性繫結至字串。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  

   > [!NOTE]
   >  如果您要產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]並且選取現有的 WCF SAP 傳送埠，您不需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  
   > 
   > [!IMPORTANT]
   >  如果您使用 SAP SNC 程式庫來連接到 SAP 系統，設定**SncLibrary**並**SncPartnerName**為適當的值。  
   > 
   >  **SncLibrary**屬性繫結採用的路徑和檔名，使用 SNC 連接到 SAP 系統所需的 Dll。 這些 Dll 必須出現在 SAP 用戶端電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。 如需詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]可在安裝指南\<安裝指南\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
   > 
   >  **SncPartnerName**屬性繫結會使用 SNC 名稱之通訊的夥伴。  

6. 按一下 [確定] 。  

7. 按一下 **[連接]**。 建立連線之後，連線狀態會顯示為**Connected**。  

    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。 圖形化使用者介面是相同的[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

    ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")  

    [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會顯示包含的各種成品，可以叫用 SAP 系統中的不同節點。 例如， **RFC**節點包含所有您連接到 SAP 系統所提供的 Rfc。 如需有關這些節點的詳細資訊，請參閱 <<c0> [ 中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  

## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中連接到 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)