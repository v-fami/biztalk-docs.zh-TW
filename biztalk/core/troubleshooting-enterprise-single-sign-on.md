---
title: 企業單一登入進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb54af9f-a6ef-46c1-b987-2019cff3f837
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ebde8c0ccbb5d266b4f244f4597aa3d71286c8a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981663"
---
# <a name="troubleshooting-enterprise-single-sign-on"></a>企業單一登入進行疑難排解
本主題描述使用企業單一登入 (SSO) 時可能遇到之常見問題的相關資訊。  

 當您開始對 SSO 環境進行疑難排解時，逐步檢查下表所列事項將有助於確保所有的元件都能如預期運作：  


|                                                                      問題                                                                      |                                                                                                                                                                                                                      註解                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                        SSO 系統中的應用程式事件記錄中是否有任何訊息？                                         | 事件記錄中的 SSO 訊息可以幫助您縮小 SSO 系統中的問題。 SSO 系統中訊息的來源是 ENTSSO。 **重要事項：** 許多 SSO 錯誤和事件顯示為警告事件記錄檔中不視為錯誤。 當問題僅影響到 SSO 服務中的單一用戶端時，SSO 會產生「警告」，而當問題影響範圍擴及整個 SSO 系統 (所有用戶端) 時，SSO 便會產生「錯誤」。 |
| SSO 服務是否安裝正確？<br /><br /> 是否依預期方式啟動？<br /><br /> SSO 服務在哪一種服務帳戶下執行？ |                                                                                                                                                               請確定 SSO 服務安裝正確，而且該服務帳戶是 SSO 系統管理員群組的成員。                                                                                                                                                                |
|                                                             SSO 資料庫在哪裡？                                                             |                                                                                                                           使用命令列 **ssoconfig -showdb**。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)。                                                                                                                           |
|                                                          正在使用哪一部 SSO 伺服器？                                                           |                                                                                                                                           使用命令列 **ssomanage -showserver**。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 如何設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)。                                                                                                                                           |
|                                                       SSO 管理員帳戶為何？                                                       |                                                                                                                         使用命令列 **ssomanage –displaydb**。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)。                                                                                                                          |
|                                                          是否已正確啟用所有項目？                                                          |                                                                                                                         使用命令列 **ssomanage –displaydb**。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)。                                                                                                                          |
|                                                        是否有分支機構應用程式？                                                        |                                                                                                                                 使用命令列 **ssomanage –listapps all**。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 列出分支機構應用程式如何](../core/how-to-list-affiliate-applications.md)。                                                                                                                                 |
|               特定的分支機構應用程式外觀是否正確？<br /><br /> 哪些帳戶正在使用此分支機構應用程式？                |                                                                                               使用命令列**ssomanage-displayapp**<em>\<應用程式名稱\></em>。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 如何列出分支機構應用程式屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)。                                                                                                |
|                                               此分支機構應用程式是否有任何對應？                                               |                                                                                                                           使用命令列**ssomanage-listmappings**<em>\<應用程式名稱\></em>。 如需有關此命令的詳細資訊，請參閱 <<c0> [ 如何列出使用者對應](../core/how-to-list-user-mappings.md)。                                                                                                                            |
|                                                    哪些帳戶是 SSO 群組的成員？                                                    |                                                                                                                                                                                            請驗證所有 SSO 群組和帳戶的群組成員資格。                                                                                                                                                                                             |
|                                          SSO 伺服器的 COM+ 應用程式的執行是否符合預期？                                           |                                                                                                                                                  驗證 COM+ 應用程式 SSO 伺服器。 **注意：** 您也可以檢查事件記錄檔的詳細資訊，例如事件和警告訊息。                                                                                                                                                  |

## <a name="known-issues"></a>已知問題  

#### <a name="entsso-service-fails-to-start"></a>ENTSSO 服務無法啟動  

##### <a name="problem"></a>問題  
 ENTSSO 服務無法啟動。  

##### <a name="cause"></a>原因  
 如果 ENTSSO 服務不是以有效的 SSO 系統管理員帳戶執行，便無法啟動。  

##### <a name="resolution"></a>解決方案  
 為 ENTSSO 服務指定有效的 SSO 系統管理員帳戶，並從服務控制管理員 (SCM) 嵌入式管理單元重新啟動服務。  

#### <a name="biztalk-services-dependent-on-the-enterprise-single-sign-on-service-entsso-fail-to-start-after-a-reboot"></a>相依於企業單一登入服務 (ENTSSO) 的 BizTalk 服務無法在重新開機後啟動  

##### <a name="problem"></a>問題  
 BTSSvc$BizTalkServerApplication 相依於企業單一登入服務 (ENTSSO)，重新開機後可能會在啟動時發生逾時。  

##### <a name="cause"></a>原因  
 企業單一登入服務可能需要約 3 分鐘的時間才能啟動。  

##### <a name="resolution"></a>解決方案  
 將 “BizTalk Service BizTalk Group：BizTalkServerApplication” 服務的啟動類型選項設定為 [自動 (延遲開始)]。 這會在所有自動服務皆完成啟動程序後，再啟動該服務。  

#### <a name="cannot-access-an-affiliate-application"></a>無法存取分支機構應用程式  

##### <a name="problem"></a>問題  
 如果與分支機構應用程式相關聯的應用程式系統管理員帳戶無效，企業單一登入服務就會停用該分支機構應用程式。  

##### <a name="cause"></a>原因  
 SSO 應用程式系統管理員帳戶無效。  

##### <a name="resolution"></a>解決方案  
 建立分支機構應用程式之前，請先確定 SSO 應用程式系統管理員帳戶是否有效。 接著，您必須啟用分支機構應用程式，才能使用該應用程式。  

#### <a name="rpc-error-occurs-when-connecting-to-a-client-computer"></a>連接到用戶端電腦時發生 RPC 錯誤  

##### <a name="problem"></a>問題  
 當使用者執行的命令這類**ssomanage-displayapp**<em>\<applicationname\></em>，其中電腦嘗試連線到遠端 SSO 伺服器以進行擷取的資訊，他們會收到下列錯誤： 錯誤： 0x800706BA: RPC 伺服器不存在。  

##### <a name="cause"></a>原因  
 當使用者指定的伺服器不正確，或是遠端伺服器上的 SSO 服務無法使用時，都會發生這個錯誤。  

##### <a name="resolution"></a>解決方案  

-   請依照下列中的步驟[如何設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)藉此確定您連線到正確的 SSO 伺服器。  

-   確定 SSO 服務已在您所連接的 SSO 伺服器上啟用及執行。  

#### <a name="master-secret-is-missing-or-corrupt"></a>主要密碼遺漏或損毀  

##### <a name="problem"></a>問題  
 主要密碼遺漏或損毀。 這個密碼通常會在設定組態時產生。 若遺漏此密碼，則企業單一登入服務啟動時，事件記錄中就會出現下列其中一則訊息。  

 MessageId=10520  

 Severity=Warning  

 SSO_WARN_NO_SECRETS  

 MessageId=10565  

 Severity=Error  

 SSO_ERROR_SECRET_VALIDATE_FAILED  

 MessageId=10521  

 Severity=Error  

 SSO_ERROR_SECRETS_NOT_LOADED  

##### <a name="cause"></a>原因  
 如果密碼是在企業單一登入服務 (SSO) 使用某個服務帳戶執行時產生，但後來服務帳戶發生變更，就有可能發生這個問題。 此密碼是以加密的形式儲存在登錄中，加密時則是使用依據服務帳戶 (用來執行 ENTSSO 者) 的識別所產生的金鑰。  

##### <a name="resolution"></a>解決方案  
 將 ENTSSO 執行時所用的服務帳戶變更為建立主要密碼時的原始服務帳戶。  

 若要變更 ENTSSO 服務帳戶：  

1.  備份主要密碼。 如需詳細資訊，請參閱 <<c0> [ 如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。  

2.  停止企業單一登入服務。  

3.  變更服務帳戶。  

4.  重新啟動 SSO，並忽略任何與密碼損毀有關的事件記錄錯誤。  

5.  還原主要密碼。 如需詳細資訊，請參閱 <<c0> [ 如何還原主要祕密](../core/how-to-restore-the-master-secret.md)。  

## <a name="see-also"></a>另請參閱  
 [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)