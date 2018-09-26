---
title: 步驟 2： 部署 Web 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb775a89-2e2d-43e5-94ae-f75c1756dbd7
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a99defc18cd38dc6f88a16b8c3fd0db2a8168426
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013119"
---
# <a name="step-2-deploy-the-web-project"></a>步驟 2： 部署 Web 專案
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 5 分鐘  
  
 在此步驟中，您將發行 Web 專案中產生[步驟 1： 建立 Web 專案中使用配接器服務開發精靈](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)網際網路資訊服務 (IIS)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成此步驟中，您應已完成[步驟 1： 建立 Web 專案中使用配接器服務開發精靈](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)。 您的 Web 伺服器也必須安裝到啟用 HTTPS 通訊的 SSL 憑證。  
  
## <a name="compile-and-deploy-the-web-project"></a>編譯及部署 Web 專案  
  
1. 在 Visual Studio 中，載入先前建立的 EchoWeb 專案。  
  
2. 開啟 Visual Studio 命令提示字元。  
  
3. 在命令提示字元中，從 C:\tutorials\echoweb 資料夾中，輸入下列命令，並按 ENTER:  
  
    **sn /k EchoWebKey.snk**  
  
    確認訊息，**金鑰組寫入 EchoWebKey.snk**，會出現在命令列。  
  
4. 關閉命令提示字元。  
  
5. 在 **方案總管**EchoWeb 專案上按一下滑鼠右鍵，然後選取**發行網站**。  
  
6. 在 [**發行網站**] 對話方塊中，如**目標位置**，輸入**http://machinename/EchoWeb**。 選取 **讓這個先行編譯的站台成為可更新**，**使用固定命名和單一頁面的組件**，並**啟用強式命名上先行編譯的組件**。 在 **機碼的檔案位置**欄位中，按一下省略符號 **（...）** 按鈕，選取先前建立的 EchoWebKey.snk 檔案，然後按一下**確定**。  
  
7. 若要確認已正確建立網站，請啟動 Internet Explorer 中，輸入 **」<http://localhost/EchoWeb/EchoOutboundContract.svc>"** 在網址列中，然後按 ENTER 鍵。 描述 EchoOutboundContractClient 網頁應該會出現。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 您只是已發行至 IIS 的 Web 專案。  
  
## <a name="next-steps"></a>後續步驟  
 既然您編譯並部署專案之後，您可以繼續進行[步驟 3： 建立應用程式定義檔案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3：在 IIS 中裝載 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)