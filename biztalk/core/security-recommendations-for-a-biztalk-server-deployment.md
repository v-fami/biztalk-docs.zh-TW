---
title: BizTalk Server 部署的安全性建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, security
- Windows Server 2003 Security Configuration Wizard (SCW)
- user accounts, security
- permissions
- access control
- security, deploying
- channel level encryption
- security, permissions
ms.assetid: 033fff11-d989-46ba-83ed-5063f7cd7818
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fad4f4a734f396b3ffec726b65fe19d62ee0f5ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22272446"
---
# <a name="security-recommendations-for-a-biztalk-server-deployment"></a>BizTalk Server 部署的安全性建議
本節包含高階、非特定功能的建議，以保護您的 Microsoft BizTalk Server 環境的安全。  
  
## <a name="topology-level-recommendations"></a>拓撲層級的建議  
 **使用通道層級加密。** 依照預設，BizTalk Server 中各元件之間的網路資料流是純文字。 若擔心訊息從一台電腦傳送到另一台電腦時遭到探查或竄改，建議您使用通道層級加密，例如網際網路通訊協定安全性 (IPSec) 或安全通訊端層 (SSL)。 因為依照預設，BizTalk Server 不會設定通道層級加密，所以 BizTalk Server 不會把加密金鑰和密碼之類的重要資料以純文字傳遞。 SSO 資料庫管理敏感性資訊的方式是使用主要密碼伺服器提供的主要密碼 (加密金鑰) 以加密的格式儲存。 依照預設，SSO 資料庫以加密的格式接收、儲存和傳送敏感性資訊。  
  
 如需有關 SSL 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/p/?LinkId=189708](http://go.microsoft.com/fwlink/p/?LinkId=189708)。  
  
 **協助確保伺服器的實體安全性。** 您也必須考慮伺服器、裝置、網路、纜線、電源供應和其他元件的實體安全性。 您應該將電腦放置在安全的環境中，並限制存取含有企業重要資訊的電腦，像是資料庫。  
  
 **只安裝您將使用的元件。** 若需要在環境中 (在周邊網路的電腦上或在執行 HTTP 和 SOAP 配接器的電腦中) 安裝 Internet Information Services (IIS)，您不需要安裝 IIS 的「檔案傳輸通訊協定」(FTP)、WebDAV 和「簡易郵件傳送通訊協定」(SMTP) 子元件。 同樣地，請確定您僅安裝和設定環境所需的 BizTalk Server 功能。 例如，僅設定您要使用的「BizTalk 訊息佇列」配接器。 如此可協助您降低環境中潛在的攻擊介面。  
  
如果使用 Internet Explorer，我們建議您開啟 Internet Explorer 增強式安全性。  
  
 **安裝 service pack 和更新**。 我們建議您一律安裝最新的產品 service pack 和 Microsoft 更新，所有在伺服器上有[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]資源，包括[!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]。  
  
 **不要在指令碼或繫結檔案中的純文字儲存密碼。** 您應該將指令碼儲存在具有強式判別存取控制清單 (DACL) 的位置，如此只有 BizTalk Server 系統管理員具有檢視、修改和執行這些指令碼的權限。 當指令碼和繫結檔案需要密碼時，務必要在使用指令碼組態或部署時遮罩密碼。 請勿將密碼以純文字保留在這些檔案中。  
  
 **使用強式判別存取控制清單 (Dacl)。** 確定您僅將資源的存取權給與使用它的使用者和帳戶，而且僅給與執行工作所需的最小權限。 將組態指令碼放置在具有 DACL 的 BizTalk Server 系統管理員的位置，請勿將純文字密碼放置在指令碼中。 確定 BizTalk Server 使用的所有服務帳戶之暫存目錄都有 DACL，如此只有該服務帳戶和 BizTalk 系統管理員具有存取權。  
  
 當您有自訂配接器時，我們建議您在具有強式 Dacl，位置儲存配接器擴充功能元件，以便只有 BizTalk Server 系統管理員具有寫入權限，這些元件。  
  
 **請不要將 BizTalk Server 放在周邊網路。** 無論公司的規模大小，將 BizTalk Server 放在周邊網路中都會使伺服器暴露於網際網路的直接攻擊和周邊網路中其他伺服器的攻擊，而可能受到危害。 因為 BizTalk Server 會與資料網域中的 Microsoft SQL Server 資料庫通訊，惡意使用者可以利用受危害的 BizTalk Server 竄改重要商務處理和組態資料。  
  
## <a name="biztalk-server-groups-and-accounts"></a>BizTalk Server 群組和帳戶  
 **使用最低權限和使用者權限的帳戶。** BizTalk Server 系統中的所有帳戶都應具有執行工作所需的最小使用者權限。 例如，您用來處理伺服器的服務帳戶不應該具有 BizTalk Server、SQL Server 或 Windows Server 的管理使用者權限。 如需詳細資訊的最小安全性權限和使用者權限的帳戶必須在 BizTalk Server 中執行的工作，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。 如需群組和 BizTalk Server 使用的帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
 **不同功能使用不同的帳戶。** 若要協助保留 BizTalk Server 環境的安全性，我們建議您為每個環境中執行的主控件執行個體建立不同的服務帳戶。 這樣也可以在密碼更新期間配置更佳的可用性。 建議一個服務帳戶不是 BizTalk server 的多個 Windows 群組的成員。  
  
 此外，我們建議您針對每個 BizTalk 主控件中，使用不同的 Windows 群組和服務帳戶屬於一個群組的成員不是另一部主機的 Windows 群組的成員。 這樣可為每個 BizTalk 主控件提供強式安全隔離。  
  
 我們建議您只是用於追蹤主控件，建立 Windows 群組，並在此群組中使用的服務帳戶，來追蹤主控件執行個體。 請勿將此服務帳戶用於其他服務，也不要使用 BizTalk 系統管理員帳戶來追蹤主控件執行個體。  
  
 **不同功能使用不同的主控件。** 我們建議您建立僅用於追蹤的主機。 設定為「主控件追蹤」的主控件擁有 MessageBox 資料庫中追蹤資料表與追蹤資料庫中資料表的讀取和寫入存取權限。 因此，在該主控件追蹤的主控件中執行的任何物件，也會擁有這些資料表的讀取和寫入存取權限。 若要封鎖使用者項目，像是管線和協調流程從潛在敏感性追蹤資料的存取，我們建議您的追蹤，而不要建立專用主控件處理、 傳送或接收訊息。  
  
 此外，我們建議您使用不同的主控件來處理、 接收和傳送訊息。 然後您可以獨立出需要存取公司私密憑證的服務帳戶。 在這些帳戶之下執行的指令碼越少，透過漏洞危害帳戶的可能性就越低，便可降低危害私密憑證的風險。  
  
 **定期變更密碼。** 您必須定期變更服務帳戶的密碼。 考量到您的主控件執行個體可能有多個服務帳戶，您必須變更這些服務帳戶的密碼。  
  
> [!CAUTION]
>  您必須變更 BizTalk 管理主控台 中的主控件執行個體的服務帳戶的密碼。 在「電腦管理」主控台中變更主控件執行個體服務帳戶的密碼會導致組態問題。  
  
 **限制 BizTalk 系統管理員群組成員資格。** BizTalk Server 系統管理員具有跨越 BizTalk Server 環境的使用者權限，包括對大部分資料 (不論加密與否) 的存取權。 因此，BizTalk 系統管理員失誤所造成的不正確組態會暴露出重要的安全性漏洞。 行為不當的 BizTalk 系統管理員會對系統造成無限的危害，包括客戶資料的機密、完整性和可用性。  
  
 若開發人員在生產環境中直接將協調流程部署到電腦，網域系統管理員必須授與開發人員 BizTalk 系統管理員使用者權限。 基於前述理由，不建議這樣做。  
  
 **限制 COM + 系統管理員群組成員資格。** 由於各種架構性因素，COM+ 系統管理員具有數個 BizTalk Server 元件的系統管理員使用者權限。 基於所有實務上的目的，您必須假設在電腦上的 COM+ 系統管理員也是 BizTalk 系統管理員，而且應該限制 BizTalk 實際伺服器中此群組的成員資格。  
  
 **讓使用者可以存取執行的服務所需的存取權的電腦。** 並非所有帳戶都需要所有電腦的權限。 BizTalk 主控件執行個體將敏感性資訊保留在記憶體中。 這些可能是像密碼或商務資訊等的重要資料。 在這些電腦上應該要設定非常嚴密的本機使用者原則。 例如，僅將這些電腦上的本機登入權限授與需要這些權限來維護部署的個人。 如此可減輕存取交換檔和損毀傾印所造成的威脅。  
  
 **限制 Power Users 群組的權限，或將它移除。** Power Users 群組的預設權限給與此群組的成員修改全電腦設定的使用者權限，包括在全域組件快取 (GAC) 中註冊的 BizTalk 組件。 每部電腦都有 GAC，包含一或多個應用程式共用的組件。 我們建議您移除變更 Power Users 群組中，從組件的權限，或您從實際 BizTalk Server 刪除 Power Users 群組。  
  
 
## <a name="see-also"></a>另請參閱  
 [群組和服務帳戶的存取控制](../core/access-control-for-groups-and-service-accounts.md)   
 [系統管理角色的存取控制](../core/access-control-for-administrative-roles.md)   
 [最低安全性使用者權限](../core/minimum-security-user-rights.md)   
 [安全性規劃](../core/planning-for-security.md)