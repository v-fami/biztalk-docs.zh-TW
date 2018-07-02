---
title: 設定 SAP 配接器的連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, specifying at run time
- connection URI, specifying at design time
ms.assetid: 8df8e4a7-13f7-48c0-8af2-451253ced7e7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88e96df27b0a8a26b20581e3ff757181ac8195cb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983047"
---
# <a name="configure-the-connection-uri-for-the-sap-adapter"></a>設定 SAP 配接器的連線 URI
連線 URI 是連接到 SAP 系統的連接字串。 它包含建立與 SAP 系統的連線所需的各種參數。 在設計階段，您必須指定要連接到 SAP 系統產生的中繼資料的 URI。 在執行階段，您必須指定要連接到 SAP 系統，來執行作業的 URI。  

## <a name="enter-the-connection-uri-at-design-time"></a>輸入連線 URI，在設計階段  
 針對設計階段，您可以指定連線 URI 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

### <a name="enter-the-connection-uri-using-consume-adapter-service-add-in"></a>輸入連線 URI 使用取用配接器服務增益集  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |             以進行此動作             |
   |----------------|------------------------------------|
   | **類別** | 按一下 **取用配接器服務**。 |
   | **範本**  | 按一下 **取用配接器服務**。 |


3. 若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4. 在**取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.  

5. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**和指定的使用者名稱和密碼來連線到 SAP 系統。  

6. 按一下  **URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  

7. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。 例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**才會產生從 SAP 系統接收 IDOC 的結構描述的屬性。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  

8. 按一下 [確定] 。  

### <a name="enter-the-connection-uri-using-add-adapter-metadata-wizard"></a>輸入連線 URI，使用 新增配接器中繼資料精靈  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |           以進行此動作            |
   |----------------|---------------------------------|
   | **類別** |     按一下 **新增介面卡**。      |
   | **範本**  | 按一下 **新增配接器中繼資料**。 |


3. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

4. 在 [新增配接器精靈] 中，選取**WCF-SAP**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  

   > [!IMPORTANT]
   >  如果您已經在 BizTalk 中設定的 WCF SAP 連接埠，請選取 從連接埠**連接埠**清單。  

5. 按 [下一步] 。  

6. 在**取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.  

7. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**和指定的使用者名稱和密碼來連線到 SAP 系統。  

8. 按一下  **URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  

9. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。 例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**才會產生從 SAP 系統接收 IDOC 的結構描述的屬性。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  

    > [!NOTE]
    >  如果您選取現有的 WCF SAP 傳送埠時，您不需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

10. 按一下 [確定] 。  

## <a name="enter-the-connection-uri-at-run-time"></a>輸入連線 URI，在執行階段  
 執行階段，您可以指定 URI 中的 WCF 自訂 」 或 「 WCF SAP 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。  

5. 在 **位址 (URI)** 文字方塊中，指定的連接來連接到 SAP 系統的 URI。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  

6. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**sapBinding**。  

7. 如果您要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   1.  選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。  

   2.  選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

8. 如果您要建立接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

   1.  選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連線到 SAP 系統。  

   2.  選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

9. 按一下 [確定] 。  

### <a name="enter-the-connection-uri-for-the-wcf-sap-port"></a>輸入 WCF SAP 連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

5. 在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。  

6. 按一下 **設定**按鈕，並提供連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  

7. 在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。  

   > [!NOTE]
   >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，繫結屬性與輸入相關的作業無法使用。 在設定傳送埠，因為輸入的作業需要接收埠組態  

8. 如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   1.  選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。  

   2.  選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

9. 如果您要建立接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

    1.  選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連線到 SAP 系統。  

    2.  選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

10. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
[建立 SAP 應用程式的建構元素](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)