---
title: 將應用程式部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04bb4496-b1e9-400b-a849-a355381849ff
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2fb0faec11638f48f0b776988a555c34c6fc62a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002815"
---
# <a name="deploying-an-application"></a>部署應用程式
部署是邏輯應用程式成品，以確保所有的必要元件都需要這些系統可以發佈點。 這些成品包括 BizTalk Server 組件、.NET 組件、 結構描述、 對應、 繫結、 商務規則和憑證。 BizTalk 應用程式可以用來協助推出到其他電腦 （當傳輸到另一個環境的應用程式） 新增至群組或預備環境的成品。  
  
 有許多方式可以部署，例如匯入應用程式的一部分使用部署精靈 （從.msi 檔案），匯入使用 BTSTask.exe、 Visual Studio 中，從部署或使用 MSBuild 的 BizTalk 成品。 如果您匯入使用 BTSTask.exe，或將其部署從 Visual Studio 中，您可以指定將它們部署到，應用程式，或將應用程式名稱留白，在此情況下部署到預設的應用程式。  
  
## <a name="deploying-by-using-an-msi-file"></a>使用.msi 檔案部署  
 使用 BizTalk Server 中，您可以藉由將它們匯出至.msi 檔案部署應用程式和其成品。 (如需有關應用程式和成品的詳細資訊，請參閱[BizTalk 應用程式是什麼？](http://go.microsoft.com/fwlink/?LinkId=154994) (<http://go.microsoft.com/fwlink/?LinkId=154994>). 匯入至 BizTalk 管理資料庫的應用程式成品，以及每個群組的成員電腦上安裝成品，牽涉到 BizTalk 應用程式的部署。 部署至.msi 檔案將序列化的所有應用程式成品成一個套件。 這可以藉由從管理主控台匯出作業，或使用 BTSTask.exe 從命令列執行。 一旦您有一個.msi 檔案時，您可以部署所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組件的 BizTalk 管理資料庫群組，或執行指令碼指定在匯入時執行。 這是藉由使用 Microsoft Management Console (MMC) 並執行匯入作業的.msi 檔案 （或透過從 BTSTASK 命令列匯入作業）。 .msi 檔案匯入作業會建立目的地 BizTalk 應用程式。  
  
 將.msi 檔案中，您可以部署在單一電腦上的應用程式，讓所有的 BizTalk Server 組件和相依性組件會儲存在全域組件快取，在電腦上。 電腦則會有所有所需的執行階段二進位檔。 在此作業中，您也可以導入的解決方案，屬於 Web 服務或指令碼來套用特定的電腦。 這項作業是由執行.msi 檔案執行。 您可以執行這項作業在執行 BizTalk Server 相關的 BizTalk 群組的成員，每一部電腦上。 您也可以使用.msi 檔案安裝應用程式新增至群組的新伺服器上。  
  
 如果您要移轉至新的群組，BizTalk 應用程式，您需要在新的群組中的所有伺服器上執行.msi 安裝。 您要匯入.msi 檔案群組的一次。 這麼做之後，應用程式和其內容在新的群組中，所有的執行階段電腦上安裝，並與群組的 BizTalk 管理 」 資料庫也已註冊。 您也可以新增多個繫結檔案至.msi 檔案，除了隱含繫結。 每個額外的繫結檔案可以是 「 環境 」 相關聯。 多個繫結檔案時 BizTalk 應用程式相關聯部署期間，您可以選擇要使用哪些繫結檔案根據您所部署的環境 （生產環境、 暫存或測試）。  
  
 您可以使用.msi 檔案的指令碼，以自訂伺服器 （安裝作業） 或群組 （匯入作業）。 如需使用.msi 檔案中的指令碼的詳細資訊，請參閱[使用自訂應用程式部署的前置和後置處理指令碼](http://go.microsoft.com/fwlink/?LinkId=154995)(http://go.microsoft.com/fwlink/?LinkId=154995)。  
  
 部署應用程式步驟的檢查清單，請參閱 <<c0> [ 檢查清單： 部署應用程式](../technical-guides/checklist-deploying-an-application.md)。  
  
## <a name="exporting-an-applications-bindings-by-using-a-binding-file"></a>使用繫結檔案匯出應用程式的繫結  
 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以匯出的繫結的繫結檔案中，應用程式，並將從繫結檔案的這些繫結匯入到另一個應用程式。 若要這樣做，必須已經存在目的端應用程式;匯入程序不會建立應用程式。 繫結檔案是 XML 檔案，其中包含應用程式、 群組或組件中的所有成品的繫結。 您也可以匯出 BizTalk 群組中，所有繫結或繫結的 BizTalk 組件。 如需有關使用繫結的詳細資訊，請參閱[如何繫結檔案匯出的繫結](../technical-guides/how-to-export-bindings-to-a-binding-file.md)並[如何從繫結檔案匯入繫結](../technical-guides/how-to-import-bindings-from-a-binding-file.md)。  
  
 您也可以新增為資源的繫結檔案至.msi 檔案。 如需有關如何將繫結檔案新增為資源的詳細資訊，請參閱[如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)。  
  
 如需有關應用程式部署在一般情況下，請參閱[了解 BizTalk 應用程式部署和管理](http://go.microsoft.com/fwlink/?LinkId=154996)(http://go.microsoft.com/fwlink/?LinkId=154996)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [部署應用程式的最佳做法](../technical-guides/best-practices-for-deploying-an-application.md)  
  
-   [部署應用程式的已知的問題](../technical-guides/known-issues-with-deploying-an-application.md)  
  
-   [管理應用程式的權限](../technical-guides/permissions-for-managing-an-application.md)  
  
-   [在應用程式中必須是唯一的成品](../technical-guides/artifacts-that-must-be-unique-in-an-application.md)  
  
-   [部署及匯出應用程式](../technical-guides/deploying-and-exporting-an-application.md)