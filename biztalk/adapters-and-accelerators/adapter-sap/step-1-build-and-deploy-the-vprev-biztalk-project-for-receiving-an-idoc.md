---
title: 步驟 1： 建立和部署接收 IDOC vPrev BizTalk 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, building and deploying previous version of BizTalk project for receiving an IDOC
- migrating, building and deploying previous version of BizTalk project for receiving an IDOC
- migration
ms.assetid: ab6bdf9a-dca5-4acd-97b2-a9afe9792978
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f99971a421530e4901c8bbac6533809a0f2f273c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963324"
---
# <a name="step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc"></a>步驟 1： 建立和部署接收 IDOC vPrev BizTalk 專案
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您要建置和部署現有的 vPrev BizTalk 專案，從 SAP 系統接收 IDOC。  
  
> [!NOTE]
>  您不需要進行任何變更 vPrev BizTalk 專案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須從 SAP 系統接收 IDOC ORDERS03 vPrev BizTalk 專案。  
  
### <a name="to-build-and-deploy-the-vprev-biztalk-project"></a>若要建置和部署 vPrev BizTalk 專案  
  
1.  建立強式名稱金鑰檔案，才能建立及部署方案。 若要建立強式名稱金鑰檔，執行下列作業：  
  
    1.  啟動 Visual Studio 命令提示字元。  
  
    2.  在命令提示字元中瀏覽至您要建立金鑰檔案的資料夾。 例如，輸入**cd C:\Sample**，然後按 ENTER 鍵。  
  
    3.  在命令提示字元中，輸入**sn-k\<金鑰檔名稱\>.snk**，然後按 ENTER 鍵。  
  
2.  以滑鼠右鍵按一下方案總管 中的 BizTalk 方案名稱，然後按一下**屬性**。 在**屬性頁**對話方塊方塊中，執行下列動作：  
  
    1.  按一下**組態屬性**從左的窗格中，並確定核取方塊，**建置**和**部署**選取資料行。  
  
    2.  按一下 **[確定]**。  
  
3.  以滑鼠右鍵按一下方案總管 中的 BizTalk 專案，然後按一下**屬性**。 在**屬性頁**對話方塊方塊中，執行下列動作：  
  
    1.  在左窗格中，依序展開**通用屬性**，然後按一下 組件。  
  
    2.  在右窗格中，在**強式名稱**類別，如**組件金鑰檔案**屬性，提供您稍早建立的組件金鑰檔案的路徑。  
  
    3.  按一下 **[確定]**。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。  
  
5.  已成功建置方案之後，以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。  
  
## <a name="next-steps"></a>後續步驟  
 建立及設定 WCF 自訂接收埠，並將它設定為從使用 WCF 為基礎的 SAP 系統接收 Idoc[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中所述，[步驟 2： 設定 Wcf-custom 單向接收埠](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)。  
  
## <a name="see-also"></a>請參閱  
 [教學課程 4：移轉 SAP 接收 IDOC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)