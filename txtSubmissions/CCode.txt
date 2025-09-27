#include <math.h>

void nW_kre(int *n, double *X, double *Y, int *m, double *g2, double *res2, double *bandwidth) {
    int N = *n;
    int M = *m;
    double h = *bandwidth;

    for (int j = 0; j < M; j++) {
        double numerator = 0.0;
        double denominator = 0.0;

        for (int i = 0; i < N; i++) {
            double u = (g2[j] - X[i]) / h;
            double w = exp(-0.5 * u * u);
            numerator += w * Y[i];
            denominator += w;
        }

        res2[j] = numerator / denominator;
    }
}
