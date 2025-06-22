# Demo CRM CI/CD Project

פרויקט לדוגמה להמחשת CI/CD עם GitHub Actions, Docker, kind ו-Kubernetes.

## מבנה הפרויקט

- `k8s/deployment.yaml` - קובץ deployment לקוברנטיס לפריסת האפליקציה
- `.github/workflows/ci-cd-pipeline.yml` - workflow ל-GitHub Actions לבנייה, בדיקה ופריסה אוטומטית

## הוראות הרצה

1. וודאו שהגדרתם סודות בגיטהאב:
   - Docker Hub: `DOCKERHUB_USERNAME` ו-`DOCKERHUB_TOKEN`
   - או GitHub Container Registry: `GHCR_TOKEN`

2. דחפו שינויים ל-branch `main` כדי להפעיל את ה-Workflow

3. להרצה ידנית ב-Killercoda:
   ```bash
   kubectl apply -f k8s/deployment.yaml
   kubectl set image deployment/demo-crm demo-crm=yourdockerusername/demo-crm:<build_number>
   kubectl rollout status deployment/demo-crm
   kubectl port-forward deployment/demo-crm 3000:3000
