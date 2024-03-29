---
title: 設定 Siebel 配接器的連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, specifying
ms.assetid: b89b60e9-0f3b-4305-865e-9d3b40d04648
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 070925b09cf4e4896097be1aa88bc57fcd625626
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992391"
---
# <a name="configure-the-connection-uri-for-the-siebel-adapter"></a>設定 Siebel 配接器的連線 URI
連線 URI 是連接至 Siebel 系統的連接字串。 連線 URI 包含建立與 Siebel 系統的連線所需的各種參數。 您必須指定此連線在設計階段和執行的階段的 URI。 在設計階段，您必須指定要連接至 Siebel 系統產生的中繼資料的 URI。 在執行階段，您必須指定要連接至 Siebel 系統來執行作業的 URI。  

## <a name="enter-the-connection-uri-at-design-time"></a>輸入連線 URI，在設計階段  
 針對設計階段，您必須指定連線 URI 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="enter-the-connection-uri-using-consume-adapter-service-add-in"></a>輸入連線 URI 使用取用配接器服務增益集  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |             以進行此動作             |
   |----------------|------------------------------------|
   | **類別** | 按一下 **取用配接器服務**。 |
   | **範本**  | 按一下 **取用配接器服務**。 |


3. 若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**siebelBinding**，，按一下 **設定**.  

5. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**和指定的使用者名稱和密碼來連接至 Siebel 系統。  

6. 在 [**設定介面卡**] 對話方塊中，按一下**URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  

7. 在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  

8. 按一下 [確定] 。  

#### <a name="enter-the-connection-uri-using-add-adapter-metadata-wizard"></a>輸入連線 URI，使用 新增配接器中繼資料精靈  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |           以進行此動作            |
   |----------------|---------------------------------|
   | **類別** |     按一下 **新增介面卡**。      |
   | **範本**  | 按一下 **新增配接器中繼資料**。 |


3. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

4. 在 [新增配接器精靈] 中，選取**Wcf-siebel**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  

   > [!IMPORTANT]
   >  如果您已經設定 biztalk Wcf-siebel 連接埠，請選取 從連接埠**連接埠**清單。  

5. 按 [下一步] 。  

6. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**siebelBinding**，，按一下 **設定**.  

7. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**和指定的使用者名稱和密碼來連接至 Siebel 系統。  

8. 在 [**設定介面卡**] 對話方塊中，按一下**URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  

9. 在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  

    > [!NOTE]
    >  如果您選取現有的 Wcf-siebel 傳送埠時，您不需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

10. 按一下 [確定] 。  

## <a name="enter-the-connection-uri-at-run-time"></a>輸入連線 URI，在執行階段  
 針對執行階段，您必須指定 URI 中的 WCF 自訂] 或 [Wcf-siebel 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

#### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開您要在其下建立連接埠，然後按一下 應用程式**傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。  

5. 在 **位址 (URI)** 文字方塊中，指定連線連接至 Siebel 系統的 URI。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  

6. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**siebelBinding**。  

7. 若要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   1.  選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。  

   2.  選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。  

8. 按一下 [確定] 。  

#### <a name="enter-the-connection-uri-for-the-wcf-siebel-port"></a>輸入連線 URI Wcf-siebel 連接埠  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [Siebel 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開您要在其下建立連接埠，然後按一下 應用程式**傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-siebel 配接器，然後按一下**設定**。  

5. 在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。  

6. 按一下 **設定**按鈕，並提供連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  

7. 在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。  

8. 若要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   1.  選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。  

   2.  選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。  

9. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
[若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)