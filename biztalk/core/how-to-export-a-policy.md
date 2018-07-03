---
title: 如何匯出原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [policies], exporting
- policies, exporting
- exporting, policies
ms.assetid: 2e46d96a-7762-479b-be20-bd590b2a4f0a
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71d697d378e48b516e3afd2ebae82cb897af12a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011463"
---
# <a name="how-to-export-a-policy"></a>如何匯出原則
本主題描述如何使用 BizTalk Server 管理主控台或命令列匯出一個或多個原則及關聯的詞彙。  
  
 匯出原則時，請牢記下列要點：  
  
-   使用 [BizTalk Server 管理主控台]，您可以從 BizTalk 群組或 BizTalk 應用程式匯出原則，並且也可以匯出詞彙。 使用 BTSTask，您可以從應用程式匯出原則，而且所有關聯的詞彙也都將匯出。 您不能選取所要匯出的詞彙。  
  
    > [!IMPORTANT]
    >  在使用管理主控台時，您可以選取要匯出哪些詞彙。 我們建議您選取匯出與原則關聯的所有詞彙。 這樣一來，您就可以確定需要的詞彙都會存在於目的地環境中。 即使需要的詞彙已經在先前部署到目的地環境，如果已刪除其關聯原則，也就會刪除這些詞彙。 這是因為當您刪除原則時，其他原則沒有使用的所有詞彙也都會被刪除。  
  
-   您可以再匯入的原則不同 BizTalk 群組，或是在不同的 BizTalk 群組中，應用程式中所述[如何匯入原則](../core/how-to-import-a-policy.md)。  
  
-   在能夠匯出原則之前，該原則必須存在於 BizTalk 群組的「規則引擎」資料庫中。 有數種方式可將原則匯入 「 規則引擎 」 資料庫中所述[如何匯入原則](../core/how-to-import-a-policy.md)。  
  
    > [!NOTE]
    >  當您使用 [規則引擎部署精靈] 從「規則引擎」資料庫移除原則後，該原則依然會出現在管理主控台中，不過您將無法予以瀏覽。 如需有關 「 規則引擎部署精靈 」 的詳細資訊，請參閱[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。  
  
-   當您使用管理主控台來匯出時，原則和詞彙都將匯出到一個 .xml 檔案中。 當您使用 BTSTask 命令列工具來匯出時，原則和詞彙都將匯出到一個應用程式 .msi 檔案中。  
  
-   BTSTask 沒有提供匯出原則的特定命令，不過您可以使用 BTSTask 的 ExportApp 命令來選擇性地只匯出您所需要的原則，而不包括其他的成品。 這樣便會產生包含原則的應用程式 .msi 檔案。 您可以使用 ImportApp 命令將 .msi 檔案匯入到不同的 BizTalk 群組中。  
  
## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  
  
-   您必須以 BizTalk Server Administrators 群組成員的帳戶登入。 如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
-   必須安裝「商務規則引擎」。 如需詳細資訊，請參閱 < [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。  
  
-   您所要匯出的原則必須存在於 BizTalk 群組的「規則引擎」資料庫中。 如果要從應用程式匯出原則，就必須也曾經將原則新增到應用程式。  
  
## <a name="to-export-a-policy"></a>若要匯出原則  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**並展開 BizTalk 群組。  
  
3. 如果您想要選取要從 BizTalk 群組上按一下滑鼠右鍵在原則的所有匯出的原則**應用程式**資料夾中，按一下**匯出**，然後按一下**原則**。  
  
    或  
  
    如果您想要匯出的原則，在特定的應用程式中，展開 應用程式 資料夾，以滑鼠右鍵按一下 應用程式，按一下**匯出**，然後按一下**原則**。  
  
    或  
  
    如果您想要匯出特定的原則，按一下 [原則] 資料夾，其中包含原則、 設定原則，以滑鼠右鍵按一下，然後按一下**匯出**。  
  
4. 在 [匯出原則] 頁面中**要匯出的原則**，選取要匯出的原則。  
  
5. 在 **要匯出詞彙**，請選取要匯出詞彙的核取方塊，並清除任何您不想要匯出的詞彙的核取方塊。 由此原則所使用的詞彙都會被自動選取。  
  
6. 在 **要匯出的檔案**中，輸入要匯出的原則或原則的 XML 檔案的路徑，然後按一下**確定**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  使用 BTSTask ListApp 命令與 /ResourceSpec 選項，來產生 XML 檔案，其中列出您想要從中匯出原則中所述的 BizTalk 應用程式中的成品[ListApp 命令](../core/listapp-command.md)。  
  
2.  編輯在上一個步驟中產生的 XML 檔案，並刪除所有的成品 (您要匯出的一個或多個原則除外)。  
  
3.  使用 BTSTask ExportApp 命令，為 /ResourceSpec 參數指定修改的 XML 檔案。 如需詳細資訊，請參閱 < [ExportApp 命令](../core/exportapp-command.md)。  
  
     BTSTask 會將指定的原則及其關聯的所有詞彙，都匯出到應用程式 .msi 檔案中。  
  
## <a name="see-also"></a>另請參閱  
 [匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [管理原則](../core/managing-policies.md)