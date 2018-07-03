---
title: 接收位置在批次處理 SQL 配接器上設定輪詢間隔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- polling interval [receive adapters]
- SQL adapters, polling interval
- receive locations, polling interval
- SQL adapters, receive locations
- receive locations, SQL adapters
ms.assetid: 9053b20d-145a-4445-b414-c0482cf975a0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: caa2c97170ff374e9acf8c1d3d4ebc7258ad69ac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005047"
---
# <a name="setting-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a>在批次處理 SQL 配接器接收位置上設定輪詢間隔
您可以設定的輪詢間隔在批次處理 SQL 配接器接收位置 (**BatchControlMessageRecvLoc**) 以不同的方式開發和生產環境的電腦上。 在程式開發伺服器上，Microsoft 建議您保持預設的 30 秒輪詢間隔，以快速啟動協議的批次處理協調流程。 然而，在實際執行伺服器上，設定為 30 秒可能會影響效能。 一旦批次已啟動，可能需要將輪詢間隔值設高一點，例如 5 分鐘。  
  
 如需合作對象的詳細資訊，請參閱[管理合作對象](../core/managing-parties.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-set-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a>若要在批次處理 SQL 配接器接收位置上設定輪詢間隔  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**BizTalk EDI 應用程式**，然後按一下**接收位置**。 以滑鼠右鍵按一下**BatchControlMessageRecvLoc**，然後按一下**屬性**。  
  
2. 在 **接收位置屬性**對話方塊中，於**傳輸**區段中，按一下**設定**。  
  
3. 在  **SQL 傳輸屬性**對話方塊方塊中，變更的值**輪詢間隔**從"30"，為所需值的預設值。 如果是實際執行伺服器，建議值為 "5"。  
  
4. 值變更**輪詢的度量單位**的預設值從**秒**來**分鐘**。  
  
5. 按一下  **確定**，然後按一下**確定**一次  
  
## <a name="see-also"></a>另請參閱  
 [管理 EDI 和 AS2 解決方案](../core/managing-edi-and-as2-solutions.md)