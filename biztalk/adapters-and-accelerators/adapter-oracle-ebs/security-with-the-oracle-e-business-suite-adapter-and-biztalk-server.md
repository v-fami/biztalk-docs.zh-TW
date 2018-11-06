---
title: Oracle E-business Suite 配接器與 BizTalk Server 安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d4a816c-505d-4d5d-9eb9-04847f9b5861
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 066ee0946210bc313188de200e695a684138e560
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752918"
---
# <a name="security-with-the-oracle-e-business-suite-adapter-and-biztalk-server"></a>Oracle E-business Suite 配接器與 BizTalk Server 安全性
當您設定傳送埠或接收埠 （位置） 使用 BizTalk Server 管理主控台或使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取 BizTalk 解決方案的訊息結構描述，您必須提供認證 for Oracle E-business Suite。 請務必在安全的方式，來協助防止它們被洩漏給潛在的惡意動作項目中提供這些認證。 本主題討論如何提供認證，最安全[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]BizTalk Server 解決方案。  
  
 更多一般討論的 BizTalk 方案的內容中的安全性是廣泛的主題，並已超出本文範圍。 如需如何讓您的 BizTalk 解決方案更安全的資訊，請參閱[安全和保護您的 BizTalk 訊息](../../core/secure-and-protect-your-biztalk-messages.md)。   
  
## <a name="how-do-i-protect-credentials-when-i-use-the-consume-adapter-service-biztalk-project-add-in-or-add-adapter-metadata-wizard"></a>如何保護認證使用時使用配接器服務 BizTalk 專案增益集，或新增配接器中繼資料精靈？  
 當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]擷取 BizTalk 解決方案的訊息結構描述，您可以提供認證以連接到 Oracle E-business Suite，在下列兩個地方：  
  
- 在 [**安全性**索引標籤中**設定配接器**] 對話方塊。 這可確保您的認證不會顯示在**設定 URI**欄位[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]對話方塊中，其中以您的電腦螢幕的存取權的任何人都可以讀取它們。  
  
- 在**OracleUserName**並**OraclePassword**上的繫結屬性**繫結屬性**索引標籤中**設定配接器** 對話方塊。 基於安全性理由**OraclePassword**繫結屬性中未提供所繫結檔案 （XML 檔案） 檔案，導致使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  > [!NOTE]
  >  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]不會產生任何繫結檔案。  
  
  如需有關如何使用以擷取訊息結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或是[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，請參閱[取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)。  
  
## <a name="how-do-i-protect-credentials-when-i-configure-a-send-port-or-a-receive-location"></a>如何保護認證時設定傳送埠或接收位置？  
 BizTalk 解決方案會使用 Microsoft BizTalk Wcf-custom 或 WCF Oracle EBS 配接器使用 WCF 服務。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是可讓用戶端使用 Oracle E-business Suite，如同一般 WCF 服務的 WCF 繫結。 BizTalk 解決方案耗用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]透過傳送埠和接收位置設定為使用 Wcf-custom 或 Wcf-oracleebs 配接器，這，接著會設定為使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]做為其傳輸。 如需如何設定傳送埠和接收的埠 （接收位置），包括如何設定 Wcf-custom 配接器的詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  

 您設定的 Oracle E-business Suite 認證**認證**索引標籤**Wcf-custom 傳輸屬性**對話方塊中的傳送埠，或從**其他**索引標籤**Wcf-custom 傳輸屬性**對話方塊的 接收位置。 由於 Wcf-custom 或 WCF Oracle EBS 配接器支援企業單一登入 (SSO)，您可以選擇提供使用者名稱和密碼，或 SSO 分支機構應用程式上的這些索引標籤。 下列主題將討論這兩個選項。  
  
### <a name="user-name-password-credentials"></a>使用者名稱密碼認證  
 您應該只提供使用者名稱和密碼**認證**（適用於傳送埠） 索引標籤或**其他**索引標籤 （如接收位置） 中**Wcf-custom 傳輸屬性** 對話方塊。 這可確保：  
  
-   您的認證不會顯示在**位址 (URI)** 對話方塊的欄位。 這會防止那些具有存取權螢幕 （或具有權限，讓他們檢視傳送埠或接收位置屬性） 看到您的認證。  
  
-   如果您要匯出的傳送埠或接收連接埠繫結，您的密碼不寫入繫結檔案。 這可防止存取的任何人從檔案檢視您的密碼。  
  
### <a name="oraclepassword-binding-property"></a>OraclePassword 繫結屬性  
 您在中指定的值**OraclePassword**繫結屬性為傳送或接收連接埠是以純文字，當您從 BizTalk Server 中的應用程式匯出繫結。 因此，從 BizTalk Server 中的應用程式匯出繫結檔案之後, 您必須手動移除的值**OraclePassword**繫結檔案中，從繫結屬性，然後再次指定每個主機上，將會使用匯出的繫結。  
  
### <a name="enterprise-single-sign-on-and-sso-affiliate-applications"></a>企業單一登入和 SSO 分支機構應用程式  
 您可以設定 Wcf-custom 配接器，使用企業單一登入 (SSO) 來取得 Oracle E-business Suite 的認證。 SSO 使用資料庫和主要祕密來加密和儲存使用者認證。 它也會提供服務，以將 Microsoft Windows 帳戶對應到第二個用來存取後端系統的認證。 藉由使用 SSO，您可以將 Windows 帳戶對應到使用者名稱和密碼的 Oracle 資料庫上。  
  
 使用 SSO*分支機構應用程式*並*SSO 對應*對應至後端系統的認證。 分支機構應用程式是指的是系統或需要次要認證的應用程式的 SSO 中的邏輯實體。 SSO 對應是與分支機構應用程式相關聯。 則會對應至該帳戶用以存取分支機構系統或應用程式的次要認證的 Windows 帳戶。 SSO 對應可以與 Windows 使用者帳戶或群組相關聯。  
  
 若要使用 SSO 與[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須執行下列動作。  
  
1.  建立來保存使用者名稱密碼認證 for Oracle E-business Suite SSO 分支機構應用程式。 具有特殊類型的 SSO 系統管理員權限的人員經常執行此步驟。  
  
2.  建立使用者或群組對應的分支機構應用程式會將您的 Windows 帳戶對應到使用者名稱和密碼用來與 Oracle 資料庫建立連線。 根據您的安裝，使用者可能無法執行此步驟中，或可能需要具有特殊類型的 SSO 系統管理員權限的某人使用。  
  
> [!NOTE]
>  為 SSO 設定時，Wcf-custom 配接器會使用提供的 SSO 服務，從 SSO 資料庫中取得 Oracle 使用者名稱和密碼。 它提供給這些 （未加密） [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，如此一來，配接器可以開啟 Oracle E-business Suite 的連線。 SSO 之間的連線提供任何加密或保護[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 Oracle E-business Suite。  
  
 如需如何使用 SSO，包括如何建立分支機構應用程式和 SSO 對應的相關資訊的詳細資訊，請參閱[使用 SSO](../../core/using-sso.md)。 如需一般 SSO 的詳細資訊，請參閱[實作企業單一登入](../../core/implementing-enterprise-single-sign-on.md)。 
  
## <a name="the-acceptcredentialsinuri-binding-property"></a>AcceptCredentialsInUri 繫結屬性  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]表面**AcceptCredentialsInUri**繫結屬性。 此屬性會決定是否允許 Oracle 資料庫或 Oracle E-business Suite 認證中的連線 URI。 根據預設， **AcceptCredentialsInUri**是**false**而[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]擲回例外狀況，如果認證包含在 URI 中。  
  
 這個屬性會顯示，因為有特定需要的認證會出現在 連線 URI 的程式設計案例。 當您要設定傳送埠或接收位置，或當您使用，這應該永遠不會是大小寫[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來擷取訊息的結構描述從[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 建議您不要設定**AcceptCredentialsInUri**要 **，則為 true**。 如需詳細資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
 **AcceptCredentialsInUri**繫結屬性不適用於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]中**繫結**同時設定 WCF 自訂 索引標籤或 Wcf-oracleebs 接收或傳送埠。 若要設定的值**AcceptCredentialsInUri**繫結屬性，您必須開啟配接器的繫結檔案 （XML 檔案），之後您已經產生中繼資料使用會建立[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，然後找出這個繫結屬性此檔案。 指定適當的值，這個繫結屬性，儲存繫結檔案，然後匯入繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 請參閱[匯入繫結](http://msdn.microsoft.com/library/7af35a2e-fb7c-48a1-af28-93427403a745)如需相關指示。  
  
## <a name="see-also"></a>另請參閱  
 [保護您的 Oracle EBS 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)  
 [若要保護的 Oracle EBS 配接器的最佳作法](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)
