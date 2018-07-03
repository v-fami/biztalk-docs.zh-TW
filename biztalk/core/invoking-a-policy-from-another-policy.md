---
title: 從另一個原則叫用 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5bf658a-02a1-426a-abe5-8c9de673cf0d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39f1366ccbf199db02bc60c0caf9015aba0cfc03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994031"
---
# <a name="invoking-a-policy-from-another-policy"></a>從另一個原則叫用原則
您可以使用下列其中一種方法，從另一個原則 (父原則) 叫用原則 (子原則)：  
  
- 呼叫**Policy.Execute**直接從父原則的方法  
  
- 呼叫的協助程式.NET 元件的方法包裝**Policy.Execute**從父原則的方法  
  
  使用第二個方法的優點是，您可以新增前置處理和後置處理程式碼來**Policy.Execute**方法。 例如，您可以在這個包裝函式方法中從子原則建立所需的任何事實。 下面幾節將提供每一個方法的範例。  
  
## <a name="invoking-the-policyexecute-method-directly-from-the-parent-policy"></a>直接從父原則叫用 Policy.Execute 方法  
 此章節提供使用叫用子原則，從父原則的高層級步驟**Policy.Execute**直接方法。  
  
### <a name="adding-the-policyexecute-action-to-the-parent-policy"></a>將 Policy.Execute 動作加入到父原則  
 下列程序中的步驟來新增**Policy.Execute**方法當做動作給父原則，將 XML 文件當做事實傳遞給子原則。  
  
##### <a name="to-add-the-policyexecute-method-as-an-action-to-a-policy"></a>若要將 Policy.Execute 方法當做動作加入到原則  
  
1.  在 事實總管 視窗中，按一下 **.NET 類別** 索引標籤。  
  
2.  以滑鼠右鍵按一下 **.NET 組件**，然後按一下**瀏覽**。  
  
3.  選取  **Microsoft.RuleEngine**從 **.NET 組件**清單，然後再按**確定**。  
  
4.  依序展開**原則**。  
  
5.  拖曳**Execute (Object facts)** 或是**Execute （Object facts，IRuleSetTrackingInterceptor trackingInterceptor）** 到 [THEN] 窗格。  
  
6.  按一下  **XML 結構描述**節點。  
  
    > [!NOTE]
    >  在這個案例中，當做事實提交給父原則的 XML 文件會當做事實傳遞給子原則。 您可以改為叫用會針對子原則建立事實的 .NET 方法。  
  
7.  以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。  
  
8.  選取您想要傳遞為事實，然後按一下 XML 文件的結構描述**開啟**。  
  
9. 拖曳*\<結構描述名稱\>* 的第一個引數的.xsd **Policy.Execute**方法以傳遞給子原則的事實傳遞給父原則的 XML 文件。  
  
10. 如果您使用**Execute**方法不接受**IRuleSetTrackingInterceptor**做為第二個引數，請略過下列步驟。  
  
11. 按一下 [ **.NET 類別**] 索引標籤。  
  
12. 拖曳**DebugTrackingInterceptor**中**Microsoft.RuleEngine**的第二個引數**Policy.Execute**方法。  
  
    > [!NOTE]
    >  如果您執行此動作時，用戶端都必須通過的執行個體**DebugTrackingInterceptor**當做事實到父原則中，依序將執行個體當做事實傳遞給子原則的類別。 相反地，您可以拖曳的建構函式**DebugTrackingInterceptor**類別，因此為您自動建立的執行個體。  
  
### <a name="modifying-the-client-application-that-invokes-the-parent-policy"></a>修改叫用父原則的用戶端應用程式  
 叫用父原則的用戶端建立的執行個體**原則**子原則名稱做為參數的類別並將它當做事實傳遞給父原則，連同其他事實。 下列範例程式碼將說明這個動作：  
  
```  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
Policy policy = new Policy("ParentPolicy");  
object[] facts = new object[3];  
facts[0] = txd;  
facts[1] = new Policy("ChildPolicy");  
facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
 如果用戶端為 BizTalk 協調流程，您可能需要的程式碼放到建立事實**運算式**圖形，然後再傳遞做為參數的 事實**呼叫規則**圖形。  
  
## <a name="invoking-a-net-wrapper-method-from-the-parent-policy"></a>從父原則叫用 .NET 包裝函式方法  
 此章節提供叫用包裝對呼叫的.NET 方法的高階步驟**Policy.Execute**從父原則的方法。  
  
### <a name="creating-the-utility-net-class"></a>建立公用程式 .NET 類別  
  
##### <a name="to-create-the-utility-class"></a>若要建立公用程式類別  
  
1.  建立 .NET 類別庫專案，然後將類別加入此專案中。  
  
2.  新增呼叫靜態方法**Policy.Execute**方法叫用原則，其名稱傳遞做為參數，如下列範例程式碼所示：  
  
    ```  
    public static void Execute(string policyName, TypedXmlDocument txd)  
    {  
        DebugTrackingInterceptor dti = new   DebugTrackingInterceptor("PolicyTracking.txt");  
        Policy policy = new Policy("ParentPolicy");  
        object[] facts = new object[3];  
        facts[0] = txd;  
        facts[1] = new Policy("ChildPolicy");  
        facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
        policy.Execute(facts, dti);  
        policy.Dispose();  
    }   
    ```  
  
3.  請確定**StaticSupport**登錄機碼設為 1 或 2。 如需詳細的登錄機碼的詳細資訊，請參閱[叫用類別的靜態成員](../core/invoking-static-members-of-a-class.md)。  
  
    > [!NOTE]
    >  您可以使用執行個體方法，而不是靜態方法。 請記得，如果您使用執行個體方法，用戶端必須將協助程式 .NET 類別的執行個體當做事實傳遞給父原則。  
  
### <a name="modifying-the-client-application"></a>修改用戶端應用程式  
 用戶端叫用父原則，然後父原則叫用會叫用子原則的協助程式方法。 用戶端的範例程式碼如下所示：  
  
```  
facts[0] = txd;  
facts[1] = new PolicyExecutor(txd);  
//call the first or parent policy  
Policy policy = new Policy(policyName);  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
> [!NOTE]
>  如果此方法為執行個體方法，用戶端必須建立協助程式 .NET 類別的執行個體，並將它當做事實傳遞給父原則。  
  
> [!NOTE]
>  如果用戶端為 BizTalk 協調流程，您可能需要的程式碼放到建立事實**運算式**圖形，然後再傳遞做為參數的 事實**呼叫規則**圖形。