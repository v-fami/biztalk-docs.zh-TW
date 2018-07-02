---
title: 設定登入認證，siebel |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, specify credentials for the Siebel system at run time
- credentials, specifying
- how to, specify credentials for the Siebel system at design time
ms.assetid: a9fef2ba-c38e-44f7-84a3-b6a95d4dc210
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ca773a4e7cd5c1d600f82b3af7b471929cff212
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971855"
---
# <a name="configure-the-sign-in-credentials-for-the-siebel"></a>設定登入認證，siebel
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]需要配接器用戶端，以提供用戶端認證。 使用 Siebel 系統驗證使用者，並建立連線，配接器會使用這些認證。  

 配接器用戶端可以提供用戶端認證是在設計階段或執行階段。 在設計階段認證，才能產生中繼資料。 在執行階段，認證才能在 Siebel 系統上執行作業。 本節提供在設計階段和執行的階段指定用戶端認證的相關資訊。  

## <a name="enter-the-client-credentials-at-design-time"></a>在設計階段中輸入用戶端認證  
 針對設計階段中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="enter-client-credentials-using-consume-adapter-service-add-in"></a>輸入 取用配接器服務增益集所使用的用戶端認證  

1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  

2.  在 **加入產生的項目**對話方塊方塊中，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**類別**|按一下 **取用配接器服務**。|  
    |**範本**|按一下 **取用配接器服務**。|  

3.  若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4.  在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**siebelBinding**，然後按一下 **設定**。  

5.  中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接至 Siebel 系統。  

6.  按一下 [確定] 。  

#### <a name="enter-client-credentials-using-add-adapter-metadata-wizard"></a>輸入用戶端認證，使用 新增配接器中繼資料精靈  

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

6. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**siebelBinding**，然後按一下 **設定**。  

7. 中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接至 Siebel 系統。  

8. 按一下 [確定] 。  

## <a name="enter-client-credentials-at-run-time"></a>在執行階段輸入用戶端認證  
 針對執行階段，您必須指定用戶端認證中的 WCF 自訂] 或 [Wcf-siebel 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

#### <a name="enter-credentials-for-the-wcf-custom-port"></a>WCF 自訂連接埠輸入認證  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，並按一下 **傳送埠**. 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

4. 傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。  

   -   選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。  

5. 按一下 [確定] 。  

> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] 也支援企業單一登入 (ESSO) 系統。 ESSO 才適用在 BizTalk 案例中，WCF 配接器是留意 ESSO 分支機構應用程式。 如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。

#### <a name="enter-credentials-for-the-wcf-siebel-port"></a>輸入認證 Wcf-siebel 連接埠  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [Siebel 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，並按一下 **傳送埠**. 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-siebel 連接埠，然後按一下**設定**。  

5. 傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。  

   -   選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。  

6. 按一下 [確定] 。  

> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] 也支援企業單一登入 (ESSO) 系統。 ESSO 才適用在 BizTalk 案例中，WCF 配接器是留意 ESSO 分支機構應用程式。 如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。

## <a name="see-also"></a>另請參閱  
[若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)